---
ms.openlocfilehash: 8a1e2ca0790cb62e3c2c879f2ba0bb169ef07d77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804359"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage již nevyvolá pro znovu vstupující implementace zprávy IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Podrobnosti|Před rozhraním .NET Framework 4.6.1 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> by <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> volání <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> s <xref:System.Windows.Forms.Application.DoEvents>a, které <xref:System.IndexOutOfRangeException?displayProperty=name>volalo nebo (a také voláno) způsobilo .<p/>Počínaje aplikacemi zaměřenými na rozhraní .NET Framework 4.6.1 již tato výjimka není vyvolána a mohou být použity filtry pro opětovné zahájení.|
|Návrh|Uvědomte <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> si, že již nebude <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> házet pro re-účastníka chování popsané výše. To se týká pouze aplikací, které cílí na rozhraní .NET Framework 4.6.1.Aplikace, které cílí na rozhraní .NET Framework 4.6.1, se mohou odhlásit z této změny (nebo aplikace, které cílí na starší architektury, se mohou přihlásit) pomocí přepínače kompatibility [DontSupportReentrantFilterMessage.](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation)|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|
