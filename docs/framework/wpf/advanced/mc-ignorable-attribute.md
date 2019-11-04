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
ms.openlocfilehash: d8fdeec8784c9a44c9b272a0a5a8b9c56ace5230
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458827"
---
# <a name="mcignorable-attribute"></a>mc:Ignorable – atribut
Určuje, které [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] předpony oboru názvů, které se vyskytly v souboru označení, může být ignorována [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]m procesorem. Atribut `mc:Ignorable` podporuje kompatibilitu značek pro vlastní mapování oboru názvů a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správu verzí.  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Použití atributu XAML (jedna předpona)  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>Použití atributu XAML (dvě předpony)  
  
```xaml  
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
|*ThisElementCanBeIgnored*|Element, který může být ignorován pomocí implementace [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] procesoru, pokud nelze přeložit nadřízený typ.|  
  
## <a name="remarks"></a>Poznámky  
 Předpona oboru názvů `mc` [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] je doporučená konvence předpony, která se má použít při mapování `http://schemas.openxmlformats.org/markup-compatibility/2006`oboru názvů kompatibility [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Prvky nebo atributy, kde předpona v názvu elementu je identifikována jako `mc:Ignorable` nevyvolává chyby při zpracování procesorem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Pokud tento atribut nelze přeložit na nadřízený typ nebo konstruktor programování, je tento prvek ignorován. Upozorňujeme však, že ignorované prvky mohou stále generovat další chyby analýzy pro další požadavky na prvky, které jsou vedlejšími účinky tohoto prvku nezpracovávány. Například určitý model obsahu elementu může vyžadovat přesně jeden podřízený element, ale pokud byl zadaný podřízený element v předponě `mc:Ignorable` a zadaný podřízený element nelze přeložit na typ, pak procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] může vyvolat chybu.  
  
 `mc:Ignorable` se vztahuje pouze na mapování oboru názvů na řetězce identifikátorů. `mc:Ignorable` se nevztahuje na mapování oboru názvů na sestavení, která určují obor názvů CLR a sestavení (nebo výchozí hodnotu pro aktuální spustitelný soubor jako sestavení).  
  
 Pokud implementujete [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor, vaše implementace procesoru nesmí vyvolávat analýzu nebo zpracování chyb na rozlišení typu pro libovolný element nebo atribut, který je kvalifikován předponou identifikovanou jako `mc:Ignorable`. Ale vaše implementace procesoru stále může vyvolávat výjimky, které jsou druhotným výsledkem selhání elementu, který se nedaří načíst nebo zpracovat, jako je například příklad prvku s jedním podřízeným objektem uvedeným dříve.  
  
 Ve výchozím nastavení bude procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorovat obsah v rámci ignorovaného prvku. Můžete však zadat další atribut, [MC: ProcessContent atribut](mc-processcontent-attribute.md), aby bylo možné pokračovat ve zpracování obsahu v rámci ignorovaného prvku následujícím dostupným nadřazeným elementem.  
  
 V atributu lze zadat více předpon s použitím jednoho nebo více prázdných znaků jako oddělovače, například: `mc:Ignorable="ignore1 ignore2"`.  

 Obor názvů `http://schemas.openxmlformats.org/markup-compatibility/2006` definuje další prvky a atributy, které nejsou zdokumentovány v této oblasti sady SDK. Další informace najdete v tématu [specifikace kompatibility značek XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Markup.XamlReader>
- [PresentationOptions:Freeze – atribut](presentationoptions-freeze-attribute.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
