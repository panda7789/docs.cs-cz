---
title: 'Omezení rizik: Implementace vlastních IMessageFilter.PreFilterMessage'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78d8ba7f872095920e7fda727f46fc10b989ed37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388284"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Omezení rizik: Implementace vlastních IMessageFilter.PreFilterMessage
V aplikacích Windows Forms, které cílové verze rozhraní .NET Framework od verze [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], vlastní <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace můžete bezpečně filtru zpráv, když <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda je volána, pokud <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementace:  
  
-   Provede jedno nebo obě z následujících akcí:  
  
    -   Přidá filtr zpráv voláním <xref:System.Windows.Forms.Application.AddMessageFilter%2A> metoda.  
  
    -   Odebere filtr zpráv voláním <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> metoda. Metoda.  
  
-   **A** čerpadla zprávy voláním <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metoda.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní pouze aplikace Windows Forms, které cílové verze rozhraní .NET Framework od verze [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Pro aplikace Windows Forms, které cílí na předchozích verzích rozhraní .NET Framework, throw takové implementace v některých případech <xref:System.IndexOutOfRangeException> výjimka při <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> metoda je volána.  
  
## <a name="mitigation"></a>Zmírnění  
 Pokud se tato změna není žádoucí, aplikace, která cílí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo novější verze můžete vyjádření výslovného nesouhlasu se přidáním následující nastavení konfigurace na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />   
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozích verzích rozhraní .NET Framework, ale běží v rámci [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] nebo novější verze můžete vyjádřit výslovný souhlas pro toto chování přidáním následující nastavení konfigurace na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)oddílu konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
