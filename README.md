 Which five elements did you find most challenging to implement and why?
<form> with multiple input types — Getting the upload section right took the most trial and error. I needed a mix of input types working together: a text field for the topic name, a type="file" input that accepts multiple file formats (.txt,.pdf,.docx) and multiple files at once, a <textarea> as a fallback for pasted notes, a <select> dropdown for confidence rating, and a date input with a min attribute so users can't pick an exam date in the past. Wrapping it all in a <fieldset> with a <legend> ("Add a topic") was the part I almost skipped, but it made the form actually read as one logical group instead of a pile of unrelated fields.

<progress> — This one looked simple but wasn't intuitive at first. I wanted a visual priority bar for each topic, and <progress value="90" max="100"> does exactly that, but I had to remember it needs fallback text between the tags (I used "90%") for browsers or screen readers that don't render it as a bar.

<details> / <summary> — Getting a native, no-JavaScript collapsible FAQ ("Why does confidence affect the schedule?") working was satisfying once I realized the browser handles the open/close state for free — no click handlers needed.

<figure> / <figcaption> — Deciding when an image deserves its own <figure> versus just sitting in a paragraph took some thought. I settled on using it for the timetable preview screenshot since it's referenced content with a caption, not just decoration — so it needed alt text describing what the image actually shows, not just a filename.

<blockquote cite="..."> — Attributing the APA quote correctly meant learning that the cite attribute takes a URL (invisible to users, but useful metadata) rather than the visible attribution text, which I had to write separately as a line inside the quote.

2) How did you use semantic elements?

I tried to make the whole page structure describe itself rather than relying on generic <div>s everywhere:

<header> holds the site title and intro tagline, with <nav aria-label="Main navigation"> inside it for the anchor-link menu — the aria-label is there so screen reader users hear "Main navigation" announced, not just "navigation" with no context.
<main> wraps everything that's the actual page content (as opposed to header/footer chrome), which helps assistive tech users jump straight to it.
<section> breaks the page into its real topic areas — intro, upload, focus, tips, about — each with its own heading, rather than one long scroll of unlabeled content.
<article> is used specifically for the two exam-tip write-ups, since each one is a self-contained piece of advice that could theoretically stand alone or be pulled out and reused elsewhere.
<aside> holds the priority-score explanation — it's related context, not core content, so it made sense to mark it as tangential.
<abbr title="Electrical Engineering">EE</abbr> and <mark> (highlighting "lecture notes, slides, and readings") add small semantic hints — one expands an abbreviation on hover/for screen readers, the other flags text as relevant/highlighted rather than just bold.
<address> wraps my contact email and GitHub link in the footer, since that's literally contact information for the document's author.
<footer> closes it out with copyright info, separate from <main>.
