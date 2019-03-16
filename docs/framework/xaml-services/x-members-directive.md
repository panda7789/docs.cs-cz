---
title: x:Members – direktiva
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: d23e6b459af932e0a6f69309f26a1cce70a9d256
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58034505"
---
# <a name="xmembers-directive"></a>x:Members – direktiva
Obsahuje sadu členů, které jsou definovány v kódu, které platí pro x: Class nadřazeného elementu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`className`|Název základní třídy nebo částečné třídy pro produkční prostředí XAML. Viz poznámky.|  
|`oneOrMoreMembers`|Jeden nebo více elementů objektu, které představují definice členů. Obvykle jde o `x:Property` objektu elementy. Viz poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 V implementaci rozhraní .NET Framework XAML Services neexistuje žádné základní třídy nebo základní implementace členu pro `x:Members`. `x:Members` je speciální člena XAML, který může existovat jako člen na libovolného typu. V datovém proudu uzlu XAML `x:Members` je vyjádřena jako člen s názvem `Members`, z oboru názvů jazyka XAML XAML. Člen `Members` obsahuje jen pro čtení obecný seznam `Member` objekty. V typické označení jednotlivé členy jsou určeny jako `x:Property` prvcích vlastností. `x:Property` je přesnější typ speciálně pro vlastnosti typů a přiřadit `x:Member`. Další informace najdete v tématu [x: Property – direktiva](x-property-directive.md).  
  
 Pro podporu praktické využití `x:Members` jako prostředek k určení definice členů v kódu, musí být členy přidružené třídy, která je možné upravit. Zamýšlený modelu je, že `x:Members` existuje jako člen typu, který určuje `x:Class`. Mechanismus pro přidružení typů a členů nebo pro vytváření dynamických členů definice však není podporován na úrovni rozhraní .NET Framework XAML Services. To je ponecháno pro jednotlivé platformy, které mají aplikačních modelů, které podporují definice členů z XAML. Obvykle akce sestavení nástroje MSBUILD, které značky kompilace XAML a buď ji integrovat s kódem na pozadí nebo vytvořit čistě z XAML sestavení jsou potřeba pro podporu této funkce.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: Members pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Members` obsahuje členy vlastní aktivity skládá zcela v XAML a XAML – definované dynamičtí členové pro Návrhář aktivity s kódem na pozadí. `x:Class` musíte také uvést v kořenovém elementu XAML výroby. Není vyžadována na úrovni rozhraní .NET Framework XAML Services, ale požadavek se změní, pokud produkční XAML je načten akcemi MSBUILD sestavení, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně. `x:Members` musí být první podřízený element ve značce elementu objektu, který deklaruje `x:Class`.
