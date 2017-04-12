===============
dolmen.builtins
===============

`dolmen.builtins` provides a collection of interfaces representing the
commonly used Python built-ins. It aims to make the component
architecture useable with the most basic objects and to defines the
types in order to extend them conveniently.

  >>> from zope.interface import verify
  >>> from dolmen.builtins import interfaces as base

  >>> macduff = b"Tis' a very nice string."
  >>> base.IString.providedBy(macduff)
  True

  >>> macbeth = u"Aye, indeed my friend."
  >>> base.IUnicode.providedBy(macbeth)
  True

  >>> is_usurper = True
  >>> base.IBoolean.providedBy(is_usurper)
  True

  >>> crown = 1
  >>> base.INumeric.providedBy(crown)
  True

  >>> king = 0.1
  >>> base.INumeric.providedBy(king)
  True

More complex types have more information defined in their interfaces.
It's the case for iterables and file-like classes.

  >>> murderers = ('MacBeth', 'Lady MacBeth')
  >>> base.ITuple.providedBy(murderers)
  True

  >>> victims = ['Banco', 'Duncan']
  >>> base.IList.providedBy(victims)
  True

  >>> thanes = {"Glamis": "MacBeth", "Fife": "MacDuff"}
  >>> base.IDict.providedBy(thanes)
  True

  >>> base.IIterable.providedBy(victims)
  True
  >>> base.IIterable.providedBy(murderers)
  True
  >>> base.IIterable.providedBy(thanes)
  True

  >>> verify.verifyObject(base.IDict, thanes)
  True

  >>> fd = open('something.txt', 'w')
  >>> base.IFile.providedBy(fd)
  True
  >>> verify.verifyObject(base.IFile, fd)
  True
