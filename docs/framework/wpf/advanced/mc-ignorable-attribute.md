---
title: mc:Ignorable – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: 25f5fb254ec6f952d7cafa2cb893e35daa0e9029
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573933"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable – atribut
Určuje, které [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] předpony oboru názvů v souboru označení může ignorovat. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru. `mc:Ignorable` Atribut podporuje kompatibility značek pro vlastní obor názvů mapování a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Použití atributu XAML (jeden předpony)  
  
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
|*ignorablePrefix ignorablePrefix1, atd.*|Libovolný platnou předponu řetězec podle specifikace XML 1.0.|  
|*ignorableUri*|Libovolný platný identifikátor URI pro určení oboru názvů, podle specifikace XML 1.0.|  
|*ThisElementCanBeIgnored*|Element, který lze ignorovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace, pokud nadřazený typ není možné přeložit.|  
  
## <a name="remarks"></a>Poznámky  
 `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] Předponu oboru názvů je předpona doporučené konvence pro použití při mapování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] oboru názvů kompatibility [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)].  
  
 Elementy nebo atributy, kde předpona názvu elementu jsou označeny jako `mc:Ignorable` nebude vyvolat chyby při zpracování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru. Pokud tento atribut nebylo možné přeložit na základní typ nebo programovací konstrukce, je tento prvek ignorován. Upozorňujeme ale, ignorované prvků může být stále generovat další chyby analýzy pro další prvek požadavky, které jsou vedlejší účinky tohoto prvku není zpracována. Například model obsahu konkrétní elementu může vyžadovat přesně jeden podřízený element, ale pokud byl zadaný podřízený element v `mc:Ignorable` předponu a zadaný podřízený element nebylo možné přeložit na typ, pak bude [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může procesor vyvolat chyby.  
  
 `mc:Ignorable` platí jenom pro mapování názvového prostoru na identifikátor řetězce. `mc:Ignorable` neplatí pro mapování názvového prostoru do sestavení, které určují [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obor názvů a sestavení (nebo výchozí aktuální spustitelného souboru jako sestavení).  
  
 Při implementaci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru, procesoru implementace nesmí vyvolat analýzu a zpracování chyb v rozlišení typů pro libovolný element nebo atribut, který je kvalifikována předponu, která je označena jako `mc:Ignorable`. Ale implementace procesoru stále může vyvolat výjimky, které jsou výsledkem sekundární nedaří načíst nebo zpracovat, jako je například dříve uvedeného příkladu jeden podřízený element elementu.  
  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor bude ignorovat obsah v rámci elementu ignorované. Můžete však zadat atribut Další [MC: processcontent – atribut](../../../../docs/framework/wpf/advanced/mc-processcontent-attribute.md), trvalé zpracování obsahu v rámci elementu ignorované podle dalšího k dispozici nadřazený element.  
  
 Dá se zadat více předpony v atribut, pomocí jednoho nebo více prázdných znaků jako oddělovač, například: `mc:Ignorable="ignore1 ignore2"`.  

 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Obor názvů definuje další prvky a atributy, které nejsou uvedené v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Další informace najdete v tématu [specifikace kompatibility značek XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze – atribut](../../../../docs/framework/wpf/advanced/presentationoptions-freeze-attribute.md)
- [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
- [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
