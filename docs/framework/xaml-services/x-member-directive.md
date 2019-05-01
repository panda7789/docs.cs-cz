---
title: x:Member – direktiva
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: 66d34ad6bc5b6bb98eba6219130035dc413b486f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951213"
---
# <a name="xmember-directive"></a>x:Member – direktiva
Deklaruje člen XAML ve značkách.  
  
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
|`className`|Název základní třídy nebo částečné třídy pro produkční prostředí XAML.|  
|`memberName`|Název člena definovaného vlastnosti.|  
  
## <a name="remarks"></a>Poznámky  
 V implementaci rozhraní .NET Framework XAML Services. `x:Member` nemá přímou typ zálohování, ale podporuje <xref:System.Windows.Markup.MemberDefinition> třídy. V datovém proudu uzlu XAML `x:Member` element je vyjádřena jako člen s názvem `Member`, z oboru názvů jazyka XAML XAML. Člen `Member` obsahuje atributy, jak je deklarován značek.  
  
 Význam `Name` a `Type` nejsou přiřazené na úrovni rozhraní .NET Framework XAML Services. V počáteční datový proud uzlu XAML jsou uloženy jako hodnoty řetězce, je interpretován později v části pravidla, která může být potřeba zavést podle konkrétní rozhraní. Význam může přizpůsobit název XAML a XAML typu, což znamená, nebo může být pouze platné v systému typů zálohování, v závislosti na implementaci.  
  
 Pro podporu praktické využití `x:Members` jako prostředek k určení definice členů v kódu, musí být členy přidružené třídy, která je možné upravit. Zamýšlený modelu je, že `x:Members` existuje jako člen typu, který určuje `x:Class`. Mechanismus pro přidružení typů a členů nebo pro vytváření dynamických členů definice však není podporován na úrovni rozhraní .NET Framework XAML Services. To je ponecháno pro jednotlivé platformy, které mají aplikačních modelů, které podporují definice členů z XAML. Obvykle akce sestavení nástroje MSBUILD, které značky kompilace XAML a buď ji integrovat s kódem na pozadí nebo vytvořit čistě z XAML sestavení jsou potřeba pro podporu této funkce.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property pro Windows Workflow Foundation  
 Pro Windows Workflow Foundation `x:Property` definuje členy vlastní aktivity skládá zcela v XAML a XAML – definované dynamičtí členové pro Návrhář aktivity s kódem na pozadí. `x:Class` musíte také uvést v kořenovém elementu XAML výroby. Není vyžadována na úrovni rozhraní .NET Framework XAML Services, ale požadavek se změní, pokud produkční XAML je načten akcemi MSBUILD sestavení, které podporují vlastní aktivity a Windows Workflow Foundation XAML obecně. Windows Workflow Foundation nepoužívá jako jeho odpovídající hodnota pro čistě název typu XAML `x:Property` `Type` atribut a místo toho používá konvenci, který nebyl zdokumentován tady. Další informace najdete v tématu [vytvoření dynamické aktivity](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
