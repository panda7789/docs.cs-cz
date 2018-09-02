---
title: x:Property – direktiva
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 34f982c30a345f95c7a1c7e70de8c5cc4de62cbb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419770"
---
# <a name="xproperty-directive"></a>x:Property – direktiva
Deklaruje vlastnost XAML ve značkách.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`className`|Název základní třídy nebo částečné třídy pro produkční prostředí XAML.|  
|`propertyName`|Název člena definovaného vlastnosti.|  
|`propertyType`|Název typu (nebo jiné formátu řetězce pro konkrétní rozhraní), který určuje typ této vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 V implementaci rozhraní .NET Framework XAML Services. `x:Property` nemá přímou typ zálohování, ale podporuje <xref:System.Windows.Markup.PropertyDefinition> třídy. V datovém proudu uzlu XAML `x:Property` element je vyjádřena jako člen s názvem `Property`, z oboru názvů jazyka XAML XAML. Člen `Property` obsahovat atributy, jak je deklarován značek.  
  
 Význam `Name` a `Type` nejsou přiřazené na úrovni rozhraní .NET Framework XAML Services. V počáteční datový proud uzlu XAML jsou uloženy jako hodnoty řetězce, je interpretován později v části pravidla, která může být potřeba zavést podle konkrétní rozhraní. Význam může přizpůsobit název XAML a XAML typu, což znamená, nebo může být pouze platné v systému typů zálohování, v závislosti na implementaci.  
  
 Pro podporu praktické využití `x:Members` jako prostředek k určení definice členů v kódu, musí být členy přidružené třídy, která je možné upravit. Zamýšlený modelu je, že `x:Members` existuje jako člen typu, který určuje `x:Class`. Mechanismus pro přidružení typů a členů nebo pro vytváření dynamických členů definice však není podporován na úrovni rozhraní .NET Framework XAML Services. To je ponecháno pro jednotlivé platformy, které mají aplikačních modelů, které podporují definice členů z XAML. Obvykle akce sestavení nástroje MSBUILD, které značky kompilace XAML a buď ji integrovat s kódem na pozadí nebo vytvořit čistě z XAML sestavení jsou potřeba pro podporu této funkce.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Property` definuje členy vlastní aktivity skládá zcela v XAML a XAML – definované dynamičtí členové pro Návrhář aktivity s kódem na pozadí. `x:Class` musíte také uvést v kořenovém elementu XAML výroby. Není vyžadována na úrovni rozhraní .NET Framework XAML Services, ale požadavek se změní, pokud produkční XAML je načten akcemi MSBUILD sestavení, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně. Windows Workflow Foundation nepoužívá jako jeho odpovídající hodnota pro čistě název typu XAML `x:Property` `Type` atribut a místo toho používá konvenci, který nebyl zdokumentován tady. Další informace najdete v tématu [vytvoření dynamické aktivity](https://msdn.microsoft.com/library/dd807392.aspx).
