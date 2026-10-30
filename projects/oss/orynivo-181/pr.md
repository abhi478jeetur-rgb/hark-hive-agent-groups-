# PR title
Improve Hindi (hi) strings: fix typo, grammar and awkward terms

# PR body
Part of #181

This is a first, smaller pass on the Hindi (`hi`) strings, as suggested in the issue. It only touches the Hindi initializer in `LocalizationManager.cs` (27 lines). No other language and no `Strings.cs` changes. All placeholders are unchanged.

What changed:
- Typo: `अजान कुंजियाँ` → `अज्ञात कुंजियाँ` (unknown keys) in the visualizer preset hint
- Grammar: `समर्थित नहीं करता` → `का समर्थन नहीं करता` (3 strings)
- Consistent terms: `विज़ुअलाइज़र`, `स्क्रॉबलिंग`, `सैंपल दर` (same spelling as the rest of the app)
- Everyday words instead of textbook Hindi: `सर्च इंडेक्स` (was `खोज सूचकांक`), `रैंडम` (was `यादृच्छिक`), `सिंक किए गए` lyrics, `पसंदीदा में जोड़ें`, `महीने`, `दिखने वाला नाम`, `Q फ़ैक्टर`
- Small meaning fixes: Toggle favorite → `पसंदीदा में जोड़ें/हटाएँ`, podcast status `डाउनलोड हो गया`, `अभी प्रसारण में`

Full old → new table with a reason for each: see below.

| Key | Old | New | Why |
|---|---|---|---|
| Visualizer | विजुअलाइजर | विज़ुअलाइज़र | Same spelling as the other visualizer strings (with nukta). |
| LastFmScrobbling | Last.fm स्क्रोब्लिंग | Last.fm स्क्रॉबलिंग | Matches 'स्क्रॉबल' used in the next string. |
| YearInReviewMonthly | माह के अनुसार सुनना | महीने के अनुसार सुनना | 'महीना' is the everyday word; app already uses 'इस महीने'. |
| MarkAsFavorite | पसंदीदा चिह्नित करें | पसंदीदा में जोड़ें | 'चिह्नित करें' reads machine-translated; Indian apps say 'पसंदीदा में जोड़ें'. |
| BulkFavorite | पसंदीदा के रूप में चिह्नित करें | पसंदीदा में जोड़ें | Same as MarkAsFavorite. |
| ToggleFavorite | पसंदीदा बदलें | पसंदीदा में जोड़ें/हटाएँ | 'पसंदीदा बदलें' means 'change favorite'; toggle = add/remove. |
| DashboardRandomPlayback | यादृच्छिक प्लेबैक | रैंडम प्लेबैक | 'यादृच्छिक' is textbook Hindi; users know 'रैंडम'. |
| SmartPlaylistSortRandom | यादृच्छिक | रैंडम | Same as above. |
| SynchronizedLyrics | समय-संयोजित | सिंक किए गए | 'समय-संयोजित' is unclear; 'सिंक किए गए' is what music apps use. |
| PlexServerName / OrynivoServerName | प्रदर्शन नाम | दिखने वाला नाम | 'प्रदर्शन' sounds like 'performance'; this is the name shown in the app. |
| ServerMissingFeatures | सर्वर समर्थित नहीं करता: {0} | सर्वर इनका समर्थन नहीं करता: {0} | Grammar: 'समर्थित नहीं करता' is wrong, needs 'का समर्थन नहीं करता'. |
| PodcastDownloaded | डाउनलोड किया | डाउनलोड हो गया | Status label, not a past action. |
| RadioNowPlaying | अभी प्रसारित | अभी प्रसारण में | 'अभी प्रसारित' is incomplete; means 'now on air'. |
| EqualizerQ | Q गुणांक | Q फ़ैक्टर | Audio users know 'Q फ़ैक्टर'; 'गुणांक' is maths textbook word. |
| Search index strings (6) | खोज सूचकांक | सर्च इंडेक्स | 'सूचकांक' is rarely used; 'सर्च इंडेक्स' is common in Indian software. |
| MaxOutputSampleRate + hint | सैम्पल रेट | सैंपल दर | Same term as 'सैंपल दर' used everywhere else in the app. |
| VisualizerPresetFolderHint | अजान कुंजियाँ | अज्ञात कुंजियाँ | Typo: 'अजान' (call to prayer) should be 'अज्ञात' (unknown). |
| MetadataDoctorServersUnavailable | Library Doctor समर्थित नहीं करते | Library Doctor का समर्थन नहीं करते | Grammar fix. |
| OrynivoReplayGainSettingsUnsupported | स्कैन सेटिंग समर्थित नहीं करता | स्कैन सेटिंग का समर्थन नहीं करता | Grammar fix. |

Check: `node scripts/verify-localization.cjs` → PASS (7 desktop locales x 1033 keys, placeholders).

Open question: "Library" is `संग्रह` in most strings but `लाइब्रेरी` in one. Happy to make it consistent in a follow-up PR, if you tell me which one you prefer.

Note: I used an AI assistant to help find and draft these fixes, and I reviewed every change myself as a native Hindi speaker.
