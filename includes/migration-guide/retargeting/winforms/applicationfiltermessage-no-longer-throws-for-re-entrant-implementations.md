---
ms.openlocfilehash: 9b184f54650d2efb31ec66f443198b19ceaeb5f3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614476"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application. FilterMessage již nevyvolává implementaci IMessageFilter. PreFilterMessage pro opětovného vstupu.

#### <a name="details"></a>Podrobnosti

Před .NET Framework 4.6.1 by volání pomocí metody, <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> která volala <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> nebo <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=fullName> (i při volání <xref:System.Windows.Forms.Application.DoEvents> ) <xref:System.IndexOutOfRangeException?displayProperty=fullName> , způsobila.<p/>Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, už tato výjimka není vyvolaná, a znovu zacílené filtry, jak je popsáno výše, se dají použít.

#### <a name="suggestion"></a>Návrh

Uvědomte si, že <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> se už nebude vyvolávat pro chování opětovného zadaného <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> postupu popsané výše. To ovlivňuje jenom aplikace cílené na .NET Framework 4.6.1. aplikace, které cílí na .NET Framework 4.6.1, si můžou tuto změnu odhlásit (nebo se můžou použít aplikace cílené na starší verze) pomocí přepínače [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) Compatibility.

| Name          | Hodnota       |
|:--------------|:------------|
| Rozsah         | Edge        |
| Verze       | 4.6.1       |
| Typ          | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType>
