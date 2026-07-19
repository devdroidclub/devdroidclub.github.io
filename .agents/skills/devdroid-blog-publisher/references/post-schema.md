# Post schema and checklist

## Current production shape

Until the project explicitly migrates, preserve the `BLOG_POSTS` structure in `index.html`:

```js
'slug-in-lowercase': {
  sourceUrl: 'https://primary.example/source',
  en: {
    tag: '/ai',
    date: 'Jul 19, 2026',
    title: 'Specific factual title',
    excerpt: 'One concise consequence-led summary.',
    body: [
      'What happened and what the source establishes.',
      'Why it matters, including limitations.',
      'Practical d.d.c. analysis connected to a service.'
    ],
    sourceLabel: 'Organization — source title'
  },
  ru: {
    tag: '/ии',
    date: '19 июля 2026',
    title: 'Конкретный фактический заголовок',
    excerpt: 'Краткое описание, начинающееся с практического следствия.',
    body: [
      'Что произошло и что подтверждает источник.',
      'Почему это важно и каковы ограничения.',
      'Практический вывод d.d.c., связанный с услугой.'
    ],
    sourceLabel: 'Организация — название источника'
  }
}
```

## Field rules

- `slug`: lowercase ASCII, digits and hyphens; stable after publication.
- `sourceUrl`: direct HTTPS primary source, not a search result.
- `tag`: one primary service-oriented category.
- `date`: publication date of the d.d.c. post; use the same calendar date in both languages.
- `title`: factual, specific, no clickbait or unsupported superlative.
- `excerpt`: consequence for the reader, not a repeated title.
- `body`: original summary and analysis; never copied source paragraphs.
- `sourceLabel`: identifiable organization and document/article name.

If multiple sources are needed, the current renderer cannot represent them cleanly. Do not silently discard them: propose a schema/UI extension or cite the primary source and mention additional verification in the review report.

## Pre-publication checklist

- [ ] Topic maps to a d.d.c. service.
- [ ] RU draft was reviewed before EN adaptation.
- [ ] Exact event and publication dates were verified.
- [ ] At least one primary source supports the central claim.
- [ ] Security, benchmark, legal, market, and financial claims have extra verification.
- [ ] Facts and d.d.c. inference are distinguishable.
- [ ] No invented metrics, testimonials, outcomes, or quotations.
- [ ] Slug is unique and route opens.
- [ ] RU and EN fields are complete.
- [ ] JavaScript syntax passes.
- [ ] Desktop/mobile and RU/EN rendering were checked, or the missing check is disclosed.
- [ ] Diff contains no unrelated change.
- [ ] User explicitly approved any commit or push.
