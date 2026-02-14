## AI

### Analyzing the prompt

**Data used:**
````
* Element's uid is 21594.
* Its selector is `ul.section-modules`
* It has 30 child element nodes: `li.module-page.complete1` (uid=21595), `li.module-page.complete1` (uid=21600), `li.module-page.complete1` (uid=21605), `li.module-page.complete1` (uid=21610), `li.module-page.complete1` (uid=21615), `li.module-page.complete1` (uid=21620), `li.module-page.complete1` (uid=21625), `li.module-page.complete1` (uid=21630), `li.module-page.complete1` (uid=21635), `li.module-page.complete1` (uid=21640), `li.module-page.complete1` (uid=21645), `li.module-page.complete2` (uid=21650), `li.module-page.complete1` (uid=21655), `li.module-page.complete1` (uid=21660), `li.module-page.complete1` (uid=21665), `li.module-page.complete1` (uid=21670), `li.module-page.complete1` (uid=21675), `li.module-page.complete2` (uid=21680), `li.module-page.complete2` (uid=21685), `li.module-page.complete2` (uid=21690), `li.module-page.complete2` (uid=21695), `li.module-page.complete2` (uid=21700), `li.module-page.complete2` (uid=21705), `li.module-page.complete2` (uid=21710), `li.module-page.complete2` (uid=21715), `li.module-page.complete2` (uid=21720), `li.module-page.complete2` (uid=21725), `li.module-page.complete2` (uid=21730), `li.module-page.complete2` (uid=21735), `li.module-page.complete2` (uid=21740)
* It doesn't have any child text nodes
* Its parent's selector is `div#coursetoc-section-modules-97` (uid=21593)
* Its parent is an element node
* Its parent has only 1 child element node
````

### List href URLs of all sibling list items

The user wants a list of `href` URLs for all the sibling `<li>` elements. I need to find the specific `<li>` element based on its innerHTML, then iterate through its siblings. For each sibling, I will find the `<a>` tag and extract its `href` attribute, along with its text content and selector for context.

**Code executed:**
```
const targetInnerHTML = "<a href=\"https://learning.iiitdwd.ac.in/mod/page/view.php?id=152&amp;forceview=1\"><span class=\"itemimage\" aria-hidden=\"true\"><img class=\"activityicon\" src=\"https://learning.iiitdwd.ac.in/theme/image.php?theme=mb2aofk&amp;component=page&amp;image=icon\" alt=\"Applied Mathematics for Data Science &amp; AI : Session - 02 on 24.05.2025\"></span><span class=\"itemname\">Applied Mathematics for Data Science &amp; AI : Session - 02 on 24.05.2025</span></a>";

const allLis = document.querySelectorAll('ul.section-modules > li');
let targetElement = null;

for (const li of allLis) {
  if (li.innerHTML === targetInnerHTML) {
    targetElement = li;
    break;
  }
}

let siblingHrefs = [];
if (targetElement && targetElement.parentNode) {
  for (const sibling of targetElement.parentNode.children) {
    if (sibling !== targetElement && sibling.nodeType === Node.ELEMENT_NODE) {
      const anchor = sibling.querySelector('a');
      if (anchor) {
        siblingHrefs.push({
          selector: sibling.tagName.toLowerCase() + (sibling.id ? `#${sibling.id}` : '') + (sibling.className ? `.${sibling.className.split(' ').join('.')}` : ''),
          textContent: sibling.textContent.trim(),
          href: anchor.href
        });
      }
    }
  }
} else if (!targetElement) {
  siblingHrefs.push({ message: 'Target element not found based on provided innerHTML.' });
}

const data = { siblingHrefs: siblingHrefs };
```

**Data returned:**
```
{"siblingHrefs":[{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 01 on 20.05.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=134&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 03 on 27.05.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=170&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 04 on 31.05.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=185&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 05 on 03.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=201&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 06 on 10.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=235&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 07 on 14.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=260&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 08 on 14.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=261&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 09 on 17.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=272&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 10 on 21.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=304&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 11 on 24.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=313&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 12 on 28.06.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=335&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 13 on 01.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=345&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 14 on 05.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=372&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 15 on 08.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=385&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 16 on 11.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=407&forceview=1"},{"selector":"li.module-page.complete1","textContent":"Applied Mathematics for Data Science & AI : Session - 17 on 12.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=408&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 18 on 19.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=451&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 19 on 26.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=488&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 20 on 29.07.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=499&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 21 on 02.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=513&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 22 on 04.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=525&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 23 on 05.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=528&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 24 on 09.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=547&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 25 on 11.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=559&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 26 on 12.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=563&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 27 on 16.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=588&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 28 on 19.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=606&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 29 on 22.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=631&forceview=1"},{"selector":"li.module-page.complete2","textContent":"Applied Mathematics for Data Science & AI : Session - 30 on 23.08.2025","href":"https://learning.iiitdwd.ac.in/mod/page/view.php?id=637&forceview=1"}]}
```

### Answer

Here are the `href` URLs for all the sibling elements of the `<li>` containing "Applied Mathematics for Data Science & AI : Session - 02 on 24.05.2025":

*   **Applied Mathematics for Data Science & AI : Session - 01 on 20.05.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=134&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 03 on 27.05.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=170&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 04 on 31.05.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=185&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 05 on 03.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=201&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 06 on 10.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=235&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 07 on 14.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=260&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 08 on 14.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=261&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 09 on 17.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=272&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 10 on 21.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=304&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 11 on 24.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=313&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 12 on 28.06.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=335&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 13 on 01.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=345&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 14 on 05.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=372&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 15 on 08.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=385&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 16 on 11.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=407&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 17 on 12.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=408&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 18 on 19.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=451&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 19 on 26.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=488&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 20 on 29.07.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=499&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 21 on 02.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=513&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 22 on 04.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=525&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 23 on 05.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=528&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 24 on 09.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=547&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 25 on 11.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=559&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 26 on 12.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=563&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 27 on 16.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=588&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 28 on 19.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=606&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 29 on 22.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=631&forceview=1`
*   **Applied Mathematics for Data Science & AI : Session - 30 on 23.08.2025**: `https://learning.iiitdwd.ac.in/mod/page/view.php?id=637&forceview=1`
