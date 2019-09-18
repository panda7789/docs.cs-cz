---
title: x:Members – direktiva
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053766"
---
# <a name="xmembers-directive"></a>x:Members – direktiva
Obsahuje sadu členů, které jsou definovány v kódu, které platí pro x:Class nadřazeného elementu.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`className`|Název záložní třídy nebo částečné třídy pro produkci XAML. Viz poznámky.|  
|`oneOrMoreMembers`|Jeden nebo více prvků objektu, které reprezentují definice členů. Obvykle jsou `x:Property` to prvky objektu. Viz poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 V implementaci .NET Framework XAML Services neexistuje žádná záložní třída ani základní implementace členů pro `x:Members`. `x:Members`je speciální člen XAML, který může existovat jako člen u libovolného typu. V datovém proudu `x:Members` uzlu XAML je reprezentován jako člen s názvem `Members`z oboru názvů XAML jazyka XAML. Člen `Members` obsahuje obecný seznam objektů, které `Member` jsou jen pro čtení. V typickém označení jsou jednotlivé členy určeny jako `x:Property` prvky vlastností. `x:Property`je přesnější typ specificky pro vlastnosti typů a lze jej `x:Member`přiřadit. Další informace najdete v tématu [direktiva x:Property](x-property-directive.md).  
  
 Aby bylo možné podporovat praktické použití `x:Members` jako způsob určení definic členů v kódu, musí být členové přidruženi ke třídě, kterou lze upravovat. Zamýšlený model `x:Members` existuje jako člen typu, který `x:Class`určuje. Mechanismus pro přidružení typů a členů nebo pro vytváření definic dynamických členů však není podporován na úrovni .NET Framework služby XAML. To je ponecháno na individuálních rozhraních, která mají modely aplikace podporující definice členů z jazyka XAML. Obvykle se akce sestavení MSBUILD, které zadávají kód, zkompiluje kód XAML a buď je integruje s kódem na pozadí, nebo vytvoří čistě ze sestavení v jazyce XAML, které jsou potřeba k podpoře této funkce.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>X:members – pro programovací model Windows Workflow Foundation  
 Pro programovací model Windows Workflow Foundation `x:Members` obsahuje členy vlastní aktivity složené výhradně v jazyce XAML, nebo XAML – definované dynamické členy pro návrháře aktivit s kódem na pozadí. `x:Class`musí být také zadáno v kořenovém elementu výroby XAML. Nejedná se o požadavek na úrovni služby .NET Framework XAML Services, ale v případě, že je výroba XAML načtena pomocí akcí sestavení MSBUILD, které podporují vlastní aktivity a programovací model Windows Workflow Foundation XAML, se ale stala požadavkem. `x:Members`musí být prvním podřízeným elementem v označení elementu Object, který deklaruje `x:Class`.
