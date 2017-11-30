---
title: "x:Members – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 230c6359c59b9f00738de9ce7ceeccd69899135f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xmembers-directive"></a>x:Members – direktiva
Obsahuje sadu členů, které jsou definovány v značek, které se vztahují na x: Class – nadřazeného elementu.  
  
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
|`className`|Název základní třídy nebo částečné třídy pro produkční XAML. V části poznámky.|  
|`oneOrMoreMembers`|Jeden či více elementů objektu, které představují definice člen. Obvykle jde o `x:Property` objektu elementy. V části poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Implementace rozhraní .NET Framework XAML Services není žádná základní třídu nebo základní člen implementaci pro `x:Members`. `x:Members`je speciální XAML člena, který může existovat jako člena na libovolného typu. V datový proud uzlu XAML `x:Members` je reprezentován jako člen s názvem `Members`, z oboru názvů jazyka XAML jazyka XAML. Člen `Members` obsahuje jen pro čtení obecné seznam `Member` objekty. V typické značek jsou jednotlivé členy zadané jako `x:Property` vlastnost elementy. `x:Property`je typu přesnější speciálně pro vlastnosti typů a přiřadit k `x:Member`. Další informace najdete v tématu [x: Property – direktiva](../../../docs/framework/xaml-services/x-property-directive.md).  
  
 Pro podporu praktické využití `x:Members` jako prostředek k zadávání definice člen v kódu, musí být přidružen třídu, která je možné upravit členy. Je určený model, který `x:Members` existuje jako člena typu, který určuje `x:Class`. Tento mechanismus pro přidružení typy a členy nebo pro vytvoření definice dynamického člena však není podporován na úrovni rozhraní .NET Framework XAML Services. To je zleva jednotlivé rozhraní, které mají modelů aplikace, které podporují definice člena z XAML. Obvykle MSBUILD sestavení akce, které kompilace kódu XAML a buď ji integrovat s nástrojem kódu nebo produktu čistě z XAML sestavení jsou potřeba k podpoře této funkce.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: Members pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Members` obsahuje členy vlastní aktivita tvoří zcela v jazyce XAML, nebo XAML – definované dynamické členy pro Návrhář aktivity s kódem v pozadí. `x:Class`musí být zadaná také v kořenovém elementu provozních XAML. To není požadavek na úrovni rozhraní .NET Framework XAML Services, ale při načtení provozní XAML akcemi MSBUILD sestavení, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně se změní na požadavek. `x:Members`musí být první podřízený prvek ve značce elementu objekt, který deklaruje `x:Class`.
