---
title: mc:ProcessContent – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: 2e93734b8ab4aefca080736db3a512f272625271
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545250"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent – atribut
Určuje, které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementy by měl mít pořád obsah zpracovává příslušné nadřazené elementy, i když může být ignorována okamžitou nadřazeného elementu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru kvůli určení [mc: Ignorovatelná atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) . `mc:ProcessContent` Podporuje atribut kompatibility značek pro vlastní obor názvů mapování i pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
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
|*ignorablePrefix*|Všechny platnou předponu řetězec podle specifikace XML 1.0.|  
|*ignorableUri*|Všechny platný identifikátor URI pro určení oboru názvů podle specifikace XML 1.0.|  
|*ThisElementCanBeIgnored*|Element, který můžete ignorovat podle [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace zpracovatelů, pokud základní typ nelze přeložit.|  
|*[obsah]*|*ThisElementCanBeIgnored* je označena Ignorovatelná. Pokud procesor ignoruje daný element *[obsah]* zpracovává *objekt*.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru bude ignorovat obsahu v rámci elementu ignorováno. Můžete zadat konkrétní element podle `mc:ProcessContent`a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru bude pokračovat ve zpracování obsahu v rámci prvku ignorováno. To by obvykle použijí, pokud je v rámci několik značek, alespoň jeden z nich je Ignorovatelná a alespoň jeden z nich není Ignorovatelná vnořený obsah.  
  
 Několik předpon je možné zadat atribut, pomocí oddělovače místo, například: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Definuje obor názvů další elementy a atributy, které nejsou popsané v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Další informace najdete v tématu [specifikace kompatibility značek XML](http://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Viz také  
 [mc:Ignorable – atribut](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
