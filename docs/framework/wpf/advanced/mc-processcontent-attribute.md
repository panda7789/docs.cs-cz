---
title: mc:ProcessContent – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: bcf55668bdc70902e346c401549a88f6ccb9072e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095122"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent – atribut
Určuje, které prvky [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] mají stále obsah zpracovaný relevantními nadřazenými prvky, a to i v případě, že je přímý nadřazený prvek možné ignorovat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ým procesorem z důvodu určení [atributu MC: ignorováno](mc-ignorable-attribute.md). Atribut `mc:ProcessContent` podporuje kompatibilitu značek pro vlastní mapování oboru názvů a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správu verzí.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*ignorablePrefix*|Libovolný platný řetězec předpony podle specifikace XML 1,0.|  
|*ignorableUri*|Libovolný platný identifikátor URI pro určení oboru názvů podle specifikace XML 1,0.|  
|*ThisElementCanBeIgnored*|Element, který může být ignorován pomocí implementace [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] procesoru, pokud nelze přeložit nadřízený typ.|  
|*sušin*|*ThisElementCanBeIgnored* je označeno jako ignorovatelné. Pokud procesor tento prvek ignoruje, je objekt *[Content]* zpracován pomocí *objektu*.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení bude procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorovat obsah v rámci ignorovaného prvku. Můžete určit konkrétní prvek pomocí `mc:ProcessContent`a procesor [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bude pokračovat ve zpracování obsahu v rámci ignorovaného prvku. Tato část by se obvykle použila v případě, že je obsah vnořen do několika značek, nejméně jeden z nich je ignorován a nejméně jeden z nich nelze ignorovat.  
  
 V atributu lze zadat více předpon pomocí oddělovače mezer, například: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 Obor názvů `http://schemas.openxmlformats.org/markup-compatibility/2006` definuje další prvky a atributy, které nejsou zdokumentovány v této oblasti sady SDK. Další informace najdete v tématu [specifikace kompatibility značek XML](https://docs.microsoft.com/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Viz také

- [mc:Ignorable – atribut](mc-ignorable-attribute.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
