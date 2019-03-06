---
title: mc:ProcessContent – atribut
ms.date: 03/30/2017
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
ms.openlocfilehash: a9af18d1fac9101a75ac16918adf8e86ef7d2ba4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357375"
---
# <a name="mcprocesscontent-attribute"></a>mc:ProcessContent – atribut
Určuje, které [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] prvky by měl mít pořád obsahu zpracovaných příslušné nadřazené elementy i v případě, že bezprostřední nadřazený element může ignorovat. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru kvůli určení [mc: ignorable – atribut](mc-ignorable-attribute.md) . `mc:ProcessContent` Atribut podporuje kompatibility značek pro vlastní obor názvů mapování a pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] správy verzí.  
  
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
|*ignorablePrefix*|Libovolný platnou předponu řetězec podle specifikace XML 1.0.|  
|*ignorableUri*|Libovolný platný identifikátor URI pro určení oboru názvů, podle specifikace XML 1.0.|  
|*ThisElementCanBeIgnored*|Element, který lze ignorovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementace, pokud nadřazený typ není možné přeložit.|  
|*[obsah]*|*ThisElementCanBeIgnored* označen jako ignorable. Pokud procesor ignoruje tento prvek *[obsah]* zpracovává *objekt*.|  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor bude ignorovat obsah v rámci elementu ignorované. Můžete zadat konkrétní elementu podle `mc:ProcessContent`a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesor bude pokračovat ve zpracování obsahu v rámci elementu ignorované. To by obvykle použijí, pokud obsah je vnořená v rámci několik značek, nejméně jeden z nich je možné ignorovat, a nejméně jeden z nich není ignorable.  
  
 Několik předpon je možné zadat atribut, pomocí oddělovače. místo, například: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.  
  
 [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] Obor názvů definuje další prvky a atributy, které nejsou uvedené v této oblasti [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)]. Další informace najdete v tématu [specifikace kompatibility značek XML](https://go.microsoft.com/fwlink/?LinkId=73824).  
  
## <a name="see-also"></a>Viz také:
- [mc:Ignorable – atribut](mc-ignorable-attribute.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
