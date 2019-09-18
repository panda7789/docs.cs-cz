---
title: x:Member – direktiva
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: d3d023873aab2039913a78108440a2e2d4ea77fb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053741"
---
# <a name="xmember-directive"></a>x:Member – direktiva
Deklaruje člena XAML ve značce.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    <x:Member Name="propertyName"/>  
    additionalMembers  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`className`|Název záložní třídy nebo částečné třídy pro produkci XAML.|  
|`memberName`|Název člena vlastnosti, kterou definujete.|  
  
## <a name="remarks"></a>Poznámky  
 V .NET Framework implementaci služby XAML. `x:Member`nemá přímý typ zálohování, ale je podporován <xref:System.Windows.Markup.MemberDefinition> třídou. V datovém proudu `x:Member` uzlu XAML je element reprezentován jako člen s názvem `Member`, z oboru názvů XAML jazyka XAML. Člen `Member` uchovává atributy deklarované pomocí značek.  
  
 Význam `Name` a`Type` nejsou přiřazeny na úrovni .NET Framework služby XAML. Jsou uloženy v počátečním proudu uzlu XAML jako řetězcové hodnoty, aby je bylo možné interpretovat později v rámci pravidel, která mohou být uložena konkrétními rozhraními. Význam může být v souladu s názvem XAML a významem typu XAML nebo může být platný pouze v systému back-Type v závislosti na implementaci.  
  
 Aby bylo možné podporovat praktické použití `x:Members` jako způsob určení definic členů v kódu, musí být členové přidruženi ke třídě, kterou lze upravovat. Zamýšlený model `x:Members` existuje jako člen typu, který `x:Class`určuje. Mechanismus pro přidružení typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni .NET Framework služby XAML. To je ponecháno na individuálních rozhraních, která mají modely aplikace podporující definice členů z jazyka XAML. Obvykle se akce sestavení MSBUILD, které zadávají kód, zkompiluje kód XAML a buď je integruje s kódem na pozadí, nebo vytvoří čistě ze sestavení v jazyce XAML, které jsou potřeba k podpoře této funkce.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x:Property pro programovací model Windows Workflow Foundation  
 Pro programovací model Windows Workflow Foundation `x:Property` definuje členy vlastní aktivity složené výhradně v jazyce XAML nebo dynamických členů definovaných v jazyce XAML pro návrháře aktivit s kódem na pozadí. `x:Class`musí být také zadáno v kořenovém elementu výroby XAML. Nejedná se o požadavek na úrovni služby .NET Framework XAML Services, ale v případě, že je výroba XAML načtena pomocí akcí sestavení MSBUILD, které podporují vlastní aktivity a programovací model Windows Workflow Foundation XAML, se ale stala požadavkem. Programovací model Windows Workflow Foundation nepoužívá jako zamýšlenou hodnotu pro `x:Property` `Type` atribut název čistě typu XAML a místo toho používá konvenci, která zde není popsána. Další informace najdete v tématu [Vytvoření DynamicActivity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
