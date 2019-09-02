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
ms.openlocfilehash: b68909d94ad8cc5bba75b2c520db82c5ccf1b922
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206190"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable – atribut
Určuje, [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] které předpony oboru názvů, které se vyskytují v souboru označení, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může procesor ignorovat. Atribut podporuje kompatibilitu značek pro vlastní mapování oboru názvů a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správu verzí. `mc:Ignorable`  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Použití atributu XAML (jedna předpona)  
  
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
|*ignorablePrefix, ignorablePrefix1 atd.*|Libovolný platný řetězec předpony podle specifikace XML 1,0.|  
|*ignorableUri*|Libovolný platný identifikátor URI pro určení oboru názvů podle specifikace XML 1,0.|  
|*ThisElementCanBeIgnored*|Element, který může být ignorován [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementacemi procesoru, pokud nelze přeložit nadřízený typ.|  
  
## <a name="remarks"></a>Poznámky  
 Předpona [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `http://schemas.openxmlformats.org/markup-compatibility/2006`oborunázvůje doporučená konvence předpony, která se použije při mapování oboru názvů kompatibility. [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] `mc`  
  
 Prvky nebo atributy, u kterých je předpona části názvu elementu identifikována `mc:Ignorable` jako nevyvolává chyby při zpracování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesorem. Pokud tento atribut nelze přeložit na nadřízený typ nebo konstruktor programování, je tento prvek ignorován. Upozorňujeme však, že ignorované prvky mohou stále generovat další chyby analýzy pro další požadavky na prvky, které jsou vedlejšími účinky tohoto prvku nezpracovávány. Například určitý model obsahu elementu může vyžadovat přesně jeden podřízený element, ale pokud zadaný podřízený element byl v `mc:Ignorable` předponě a zadaný podřízený element nelze přeložit na typ, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pak procesor může vyvolá chybu.  
  
 `mc:Ignorable`vztahuje se pouze na mapování oboru názvů na řetězce identifikátorů. `mc:Ignorable`neplatí pro mapování oboru názvů na sestavení, která určují obor názvů CLR a sestavení (nebo výchozí hodnotu pro aktuální spustitelný soubor jako sestavení).  
  
 Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, implementace procesoru nesmí vyvolat analýzu nebo zpracování chyb v rozlišení typu pro libovolný element nebo atribut, který je kvalifikován předponou, která je identifikována jako `mc:Ignorable`. Ale vaše implementace procesoru stále může vyvolávat výjimky, které jsou druhotným výsledkem selhání elementu, který se nedaří načíst nebo zpracovat, jako je například příklad prvku s jedním podřízeným objektem uvedeným dříve.  
  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bude procesor ignorovat obsah v rámci ignorovaného prvku. Můžete však zadat další atribut, [MC: ProcessContent atribut](mc-processcontent-attribute.md), aby bylo možné pokračovat ve zpracování obsahu v rámci ignorovaného prvku následujícím dostupným nadřazeným elementem.  
  
 V atributu lze zadat více předpon, přičemž jako oddělovač použijte jeden nebo více prázdných znaků, například: `mc:Ignorable="ignore1 ignore2"`.  

 `http://schemas.openxmlformats.org/markup-compatibility/2006` Obor názvů definuje jiné elementy a atributy, které nejsou zdokumentovány v této oblasti sady SDK. Další informace najdete v tématu [specifikace kompatibility značek XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze – atribut](presentationoptions-freeze-attribute.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
