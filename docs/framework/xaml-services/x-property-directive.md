---
title: x:Property – direktiva
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: 7624014e0cd9ddd47cc84ee9686a6f11c27d1843
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053925"
---
# <a name="xproperty-directive"></a>x:Property – direktiva
Deklaruje vlastnost XAML ve značce.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType"/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`className`|Název záložní třídy nebo částečné třídy pro produkci XAML.|  
|`propertyName`|Název člena vlastnosti, kterou definujete.|  
|`propertyType`|Název typu (nebo jiný řetězcový tvar, specifický pro rozhraní), který určuje typ této vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework implementaci služby XAML. `x:Property`nemá přímý typ zálohování, ale je podporován <xref:System.Windows.Markup.PropertyDefinition> třídou. V datovém proudu `x:Property` uzlu XAML je element reprezentován jako člen s názvem `Property`, z oboru názvů XAML jazyka XAML. Atributy blokování `Property` člena deklarované pomocí značek.  
  
 Význam `Name` a`Type` nejsou přiřazeny na úrovni .NET Framework služby XAML. Jsou uloženy v počátečním proudu uzlu XAML jako řetězcové hodnoty, aby je bylo možné interpretovat později v rámci pravidel, která mohou být uložena konkrétními rozhraními. Význam může být v souladu s názvem XAML a významem typu XAML nebo může být platný pouze v systému back-Type v závislosti na implementaci.  
  
 Aby bylo možné podporovat praktické použití `x:Members` jako způsob určení definic členů v kódu, musí být členové přidruženi ke třídě, kterou lze upravovat. Zamýšlený model `x:Members` existuje jako člen typu, který `x:Class`určuje. Mechanismus pro přidružení typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni .NET Framework služby XAML. To je ponecháno na individuálních rozhraních, která mají modely aplikace podporující definice členů z jazyka XAML. Obvykle se akce sestavení MSBUILD, které zadávají kód, zkompiluje kód XAML a buď je integruje s kódem na pozadí, nebo vytvoří čistě ze sestavení v jazyce XAML, které jsou potřeba k podpoře této funkce.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x:Property pro programovací model Windows Workflow Foundation  
 Pro programovací model Windows Workflow Foundation `x:Property` definuje členy vlastní aktivity složené výhradně v jazyce XAML nebo dynamických členů definovaných v jazyce XAML pro návrháře aktivit s kódem na pozadí. `x:Class`musí být také zadáno v kořenovém elementu výroby XAML. Nejedná se o požadavek na úrovni služby .NET Framework XAML Services, ale v případě, že je výroba XAML načtena pomocí akcí sestavení MSBUILD, které podporují vlastní aktivity a programovací model Windows Workflow Foundation XAML, se ale stala požadavkem. Programovací model Windows Workflow Foundation nepoužívá jako zamýšlenou hodnotu pro `x:Property` `Type` atribut název čistě typu XAML a místo toho používá konvenci, která zde není popsána. Další informace najdete v tématu [Vytvoření DynamicActivity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
