---
title: "mc:Ignorable – atribut"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3be5949ee26fbb21d913a7aefe2664202c5bef38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="mcignorable-attribute"></a>mc:Ignorable – atribut
Určuje, které [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] předpony oboru názvů v souboru kódu může být ignorována [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru. `mc:Ignorable` Podporuje atribut kompatibility značek pro vlastní obor názvů mapování i pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Použití atributu XAML (jednu předponu)  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>Použití atributu XAML (dvě předpony)  
  
```  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*ignorablePrefix, ignorablePrefix1, atd.*|Všechny platnou předponu řetězec podle specifikace XML 1.0.|  
|*ignorableUri*|Všechny platný identifikátor URI pro určení oboru názvů podle specifikace XML 1.0.|  
|*ThisElementCanBeIgnored*|Element, který můžete ignorovat podle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace zpracovatelů, pokud základní typ nelze přeložit.|  
  
## <a name="remarks"></a>Poznámky  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Předponu oboru názvů je doporučené předponu konvence pro použití při mapování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obor názvů kompatibility [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].  
  
 Elementy nebo atributy, kde jsou předpony část název elementu označeny jako `mc:Ignorable` nevydá chyby při zpracování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru. Pokud tento atribut nelze přeložit na základní typ nebo programovací konstrukce, že element ignorován. Pozor ale ignoruje elementy může generovat stále další chyby analyzátoru element další požadavky, které jsou vedlejší účinky tohoto prvku nejsou zpracována. Model obsahu určitý element může například vyžadovat přesně jeden podřízený element, ale pokud byl zadaný podřízený element v `mc:Ignorable` předponu a zadaný podřízený element nebylo možné přeložit na typ, pak se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může procesoru vyvolá chybu.  
  
 `mc:Ignorable`platí jenom pro mapování oboru názvů na identifikátor řetězce. `mc:Ignorable`nelze použít u mapování oboru názvů do sestavení, které určují [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů a sestavení (nebo výchozí nastavení aktuální spustitelného souboru jako sestavení).  
  
 Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, implementaci procesoru nesmí vyvolat analýza nebo zpracování chyb v řešení typu pro element nebo atribut, který je kvalifikován předponu, která je označena jako `mc:Ignorable`. Ale implementaci procesoru může být stále spojeno výjimky, které jsou výsledkem sekundární elementu nedaří se načíst nebo zpracovat, jako je například jeden podřízený element zadána dříve.  
  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru bude ignorovat obsahu v rámci elementu ignorováno. Můžete však zadat atribut Další [mc:ProcessContent atribut](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), trvalá zpracování obsahu v rámci elementu ignorováno další dostupné nadřazeného elementu.  
  
 V atributu, například pomocí jednoho nebo více znaky prázdné znaky jako oddělovače, lze zadat více předpony: `mc:Ignorable="ignore1 ignore2"`.  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Definuje obor názvů další elementy a atributy, které nejsou popsané v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Další informace najdete v tématu [specifikace kompatibility značek XML](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Markup.XamlReader>  
 [Atribut PresentationOptions:Freeze](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
