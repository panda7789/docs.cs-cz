---
ms.openlocfilehash: 8a1e2ca0790cb62e3c2c879f2ba0bb169ef07d77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803700"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage již nevyvolá pro vícenásobně implementace IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Podrobnosti|Před rozhraní .NET Framework 4.6.1, volání <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> s <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> kterou volat <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> nebo <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (také věnovaly <xref:System.Windows.Forms.Application.DoEvents>) by způsobilo <xref:System.IndexOutOfRangeException?displayProperty=name>.<p/>Od verze aplikace cílené na rozhraní .NET Framework 4.6.1, tento je již vyvolána výjimka, a vícenásobně výše popsaným způsobem mohou být použity filtry.|
|Doporučení|Mějte na paměti, která <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> se již nezobrazují výjimku pro vícenásobně <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> chování popsané výše. To ovlivní pouze aplikace cílí na rozhraní .NET Framework 4.6.1 můžete vyjádřit výslovný nesouhlas tato změna cílení 4.6.1.Apps rozhraní .NET Framework (nebo aplikace cílení starší rozhraní mohou vyjádřit výslovný souhlas) s použitím [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) přepínače kompatibility.|
|Rozsah|Edge|
|Version|4.6.1|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|
