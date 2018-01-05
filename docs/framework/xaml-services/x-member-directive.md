---
title: "x:Member – direktiva"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ea04dfe5f3c371acbb388256b0854b0da8f45a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xmember-directive"></a>x:Member – direktiva
Deklaruje člena XAML v kódu.  
  
## <a name="xaml-object-element-usage"></a>Použití elementu objektu XAML  
  
```  
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
|`className`|Název základní třídy nebo částečné třídy pro produkční XAML.|  
|`memberName`|Název člena vlastnosti definovaný.|  
  
## <a name="remarks"></a>Poznámky  
 V implementaci rozhraní .NET Framework XAML Services. `x:Member`nemá přímé typ zálohování, ale podporuje <xref:System.Windows.Markup.MemberDefinition> třídy. V datový proud uzlu XAML `x:Member` element je reprezentován jako člen s názvem `Member`, z oboru názvů jazyka XAML jazyka XAML. Člen `Member` obsahuje atributů deklarovaná značek.  
  
 Význam `Name` a `Type` nejsou přiřazeny na úrovni rozhraní .NET Framework XAML Services. Jsou uložené v počáteční datový proud uzlu XAML jako řetězcové hodnoty budou interpretovat později v části pravidla, která může být způsobené konkrétní rozhraní. Význam může zarovnat na XAML název a typ jazyka XAML, což znamená, nebo může být pouze platné ve základní typ systému, v závislosti na implementaci.  
  
 Pro podporu praktické využití `x:Members` jako prostředek k zadávání definice člen v kódu, musí být přidružen třídu, která je možné upravit členy. Je určený model, který `x:Members` existuje jako člena typu, který určuje `x:Class`. Tento mechanismus pro přidružení typy a členy nebo pro vytvoření definice dynamického člena však není podporován na úrovni rozhraní .NET Framework XAML Services. To je zleva jednotlivé rozhraní, které mají modelů aplikace, které podporují definice člena z XAML. Obvykle MSBUILD sestavení akce, které kompilace kódu XAML a buď ji integrovat s nástrojem kódu nebo produktu čistě z XAML sestavení jsou potřeba k podpoře této funkce.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Property` definuje členy vlastní aktivita tvoří zcela v jazyce XAML, nebo XAML – definované dynamické členy pro Návrhář aktivity s kódem v pozadí. `x:Class`musí být zadaná také v kořenovém elementu provozních XAML. To není požadavek na úrovni rozhraní .NET Framework XAML Services, ale při načtení provozní XAML akcemi MSBUILD sestavení, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně se změní na požadavek. Windows Workflow Foundation nepoužívá jako jeho určená hodnota pro název typu čistý XAML `x:Property` `Type` atribut a místo toho používá názvů, který není dokumentováno sem. Další informace najdete v tématu [dynamické vytvoření aktivity](http://msdn.microsoft.com/library/dd807392.aspx).
