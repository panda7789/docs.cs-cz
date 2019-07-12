---
ms.openlocfilehash: 8e37007318a55188d44607fd5e4c4f3950c105df
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804359"
---
### <a name="applicationfiltermessage-no-longer-throws-for-re-entrant-implementations-of-imessagefilterprefiltermessage"></a>Application.FilterMessage již nevyvolá pro vícenásobně implementace IMessageFilter.PreFilterMessage

|   |   |
|---|---|
|Podrobnosti|Před rozhraní .NET Framework 4.6.1, volání <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> s <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> kterou volat <xref:System.Windows.Forms.Application.AddMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> nebo <xref:System.Windows.Forms.Application.RemoveMessageFilter(System.Windows.Forms.IMessageFilter)?displayProperty=name> (také věnovaly <xref:System.Windows.Forms.Application.DoEvents>) by způsobilo <xref:System.IndexOutOfRangeException?displayProperty=name>.<p/>Od verze aplikace cílené na rozhraní .NET Framework 4.6.1, tento je již vyvolána výjimka, a vícenásobně výše popsaným způsobem mohou být použity filtry.|
|Doporučení|Mějte na paměti, která <xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)> se již nezobrazují výjimku pro vícenásobně <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage(System.Windows.Forms.Message@)> chování popsané výše. To ovlivní pouze aplikace cílí na rozhraní .NET Framework 4.6.1 můžete vyjádřit výslovný nesouhlas tato změna cílení 4.6.1.Apps rozhraní .NET Framework (nebo aplikace cílení starší rozhraní mohou vyjádřit výslovný souhlas) s použitím [DontSupportReentrantFilterMessage](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md#mitigation) přepínače kompatibility.|
|Scope|Edge|
|Version|4.6.1|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.Forms.Application.FilterMessage(System.Windows.Forms.Message@)?displayProperty=nameWithType></li></ul>|

