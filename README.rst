Disable the TYPO3 "Page is being generated" message
===================================================

This extension disables the "Page is being generated" message which is shown
when two requests try to render the same page simultaneously.

Disabling that message means that all concurrent requests render the same content
independently.

TYPO3 implements the "Page is being generated" message through a
"temporary page cache" concept.
Instead of using a XCLASS, this extension hooks into the TYPO3 Caching Framework.
We simply invalidate the timeout of the aformentioned temporary cache, so
that the *temporary* content is never valid and thus never sent to the user.
This does not affect delivery of cached page contents. They will be sent as usual
as they are not marked as *temporary* cache content.

No configuration needed.
Just install:

.. code-block:: bash

   typo3/cli_dispath.phpsh extbase extension:install skip_page_is_being_generated
