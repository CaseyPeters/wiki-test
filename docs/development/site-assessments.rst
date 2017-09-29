.. title:: Site Assessments

Site Assessments
================

Sometimes we need to make site assessments on website we haven't built before
deciding to take them over, in general the main goal is to check the overall
quality of the website and see if we can work on it in the future. Some of the
things to look out for can be:

- **Magento version:** Check how old the Magento version is to see how much work it would take to update it if necessary.
- **Patches:** Check if all security patches have been applied and list all patches applied and ones not. `Mage Report`_ can help to identify this.
- **Changes to core files**: Check if any of the core files have been changed, we can use the ``diff`` cli tool to quickly spot differences against a brand new Magento installation of the same version. The main folders to look are:

  - app/code/core/
  - app/design/frontend/base/
  - js/
  - lib/
  - shell/
  - skin/frontend/base/

- **Number of extensions installed**: Usually the more extensions installed the more likely it is that something will break. List all the extensions and state whether they are enabled or disabled.
- **Local file rewrites**: Check if some of the core classes have been overwritten in the **local** folder, specially important if any of the files need to be patched.
- **Overall code quality**: Check the code style, indentation, consistency, etc., most of the time if the code is written `the Magento way` it is easier to work with.
- **Security recommendations**: Check for admin URL, downloader URL, suspect files and code, list all admin user accounts and suggest a password update.
- **Bad configuration**: Check for any config settings which aren't correct or recommend any changes.
- **Performance**: Make recommendations and notes on how the site performs and suggest ways to improve performance. Use third-party performance tools such as `Google Page Speed Insights`_, `Pingdom`_, `QuickSprout`_, or `Nibbler`_ for this if required.
- **Any other recommendations**: When looking at the site, make a note of anything else you would recommend or any things to note.

.. _Mage Report: https://www.magereport.com
.. _Google Page Speed Insights: https://developers.google.com/speed/pagespeed/insights/
.. _Pingdom: https://tools.pingdom.com
.. _QuickSprout: https://www.quicksprout.com
.. _Nibbler: http://nibbler.silktide.com