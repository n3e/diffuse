diffuse
=======

#### a python3 powered FUSE (filesystem in userspace) wrapper ####

the diffuse is a package built using python3 and ctypes library that
aims to ease development of custom filesystem implementations.

### development ###

as the diffuse is a new project of mine, a newborn baby, it is missing
a lot of features and ideas i would like to implement over the time.

the main reason i have began it for is that i had severe issues with
other FUSE wrappers ranging from version incompatibilty to quite strange
and unexpected behaviour. by the time i have understood the way some of
them worked, i had several ideas regarding the diffuse (which originally was
a name for c++0x FUSE wrapper i intended to create for the very same reason).

### targeted platforms ###

currently i am testing and developing under x64 virtualized arch linux using
FUSE version `2.8.5-1`, however i am aiming for compatibilty with other
platforms supported by FUSE in near future.

usage
-----

i would like to introduce as clean scheme as possible, enabling dynamic
customization and simple interface.

    import diffuse
    import diffuse.operator

    class helloworld(diffuse.operator.base):
        def getattr(self, path):
            return { 'mode': 0x416d }

        def readdir(self, path, id):
            return [ '.', '..', 'hello', 'world' ]

    diffuse.run(helloworld(), './mp')

the final approach choice is, however, a subject of changes and might
vary in future. i would also like to provide a set of re-usable default
`diffuse.operator` operators that would handle some basic tasks of a
custom rudimentary filesystem. 
