.. Licensed to the Apache Software Foundation (ASF) under one
.. or more contributor license agreements.  See the NOTICE file
.. distributed with this work for additional information
.. regarding copyright ownership.  The ASF licenses this file
.. to you under the Apache License, Version 2.0 (the
.. "License"); you may not use this file except in compliance
.. with the License.  You may obtain a copy of the License at
..
..  http://www.apache.org/licenses/LICENSE-2.0
..
.. Unless required by applicable law or agreed to in writing,
.. software distributed under the License is distributed on an
.. "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
.. KIND, either express or implied.  See the License for the
.. specific language governing permissions and limitations
.. under the License.

=================================
Apache TinkerPop - Gremlin Python
=================================

`Apache TinkerPop™ <http://tinkerpop.apache.org>`_
is a graph computing framework for both graph databases (OLTP) and
graph analytic systems (OLAP). `Gremlin <http://tinkerpop.apache.org/gremlin.html>`_
is the graph traversal language of
TinkerPop. It can be described as a functional, data-flow language that enables users to succinctly express complex
traversals on (or queries of) their application's property graph.

Gremlin-Python implements Gremlin within the Python language and can be used on any Python virtual machine including
the popular CPython machine. Python’s syntax has the same constructs as Java including "dot notation" for function
chaining ``(a.b.c)``, round bracket function arguments ``(a(b,c))``, and support for global namespaces
``(a(b()) vs a(__.b()))``. As such, anyone familiar with Gremlin-Java will immediately be able to work with
Gremlin-Python. Moreover, there are a few added constructs to Gremlin-Python that make traversals a bit more succinct.

Gremlin-Python is designed to connect to a "server" that is hosting a TinkerPop-enabled graph system. That "server"
could be `Gremlin Server <http://tinkerpop.apache.org/docs/current/reference/#gremlin-server>`_ or a
`remote Gremlin provider <http://tinkerpop.apache.org/docs/current/reference/#connecting-rgp>`_ that exposes
protocols by which Gremlin-Python can connect.

A typical connection to a server running on "localhost" that supports the Gremlin Server protocol using websockets
from the Python shell looks like this:

    >>> from gremlin_python.process.anonymous_traversal import traversal
    >>> from gremlin_python.driver.driver_remote_connection import DriverRemoteConnection
    >>> g = traversal().withRemote(DriverRemoteConnection('ws://localhost:8182/gremlin','g'))

Once "g" has been created using a connection, it is then possible to start writing Gremlin traversals to query the
remote graph:

    >>> g.V().both()[1:3].toList()
    [v[2], v[4]]
    >>> g.V().both()[1].toList()
    [v[2]]
    >>> g.V().both().name.toList()
    [lop, vadas, josh, marko, marko, josh, peter, ripple, lop, marko, josh, lop]

Please see the `reference documentation <http://tinkerpop.apache.org/docs/current/reference/#gremlin-python>`_
at Apache TinkerPop for more information on usage.

NOTE that versions suffixed with "rc" are considered release candidates (i.e. pre-alpha, alpha, beta, etc.) and
thus for early testing purposes only.
