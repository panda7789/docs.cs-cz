---
title: x:ClassModifier – direktiva
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: 22
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ab6036ecb37bb80588a59b581af0b88fc83230a4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier – direktiva
Mění chování kompilace XAML při `x:Class` k dispozici je také. Konkrétně, místo vytvoření částečné `class` má `Public` (výchozí), úroveň přístupu poskytnutého `x:Class` je vytvořena s `NotPublic` úroveň přístupu. Toto chování ovlivňuje úroveň přístupu pro třídy v vygenerované sestavení.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*NotPublic*|S přesným řetězcem předat zadejte <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na programovací jazyk kódu, který používáte. V části poznámky.|  
  
## <a name="dependencies"></a>Závislosti  
 [x: Class –](../../../docs/framework/xaml-services/x-class-directive.md) také je třeba zadat u stejného elementu, a tento element musí být kořenový element na stránce. Další informace najdete v tématu [ \[MS-XAML\] části 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `x:ClassModifier` v rozhraní .NET Framework XAML Services využití se liší podle programovací jazyk. Řetězec, který má použít, závisí na tom, jak každý z těchto jazyků implementuje jeho <xref:System.CodeDom.Compiler.CodeDomProvider> a převaděče typů vrátí k definování významy pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a jestli je tento jazyk velká a malá písmena.  
  
-   Pro jazyk C#, řetězec pro určení <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `internal`.  
  
-   Pro Microsoft Visual Basic .NET, řetězec pro určení <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `Friend`.  
  
-   Pro [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], neexistují žádné cíle podporující kompilování XAML; hodnotu předávání tedy neurčené.  
  
 Můžete také zadat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` v jazyce C#, `Public` v jazyce Visual Basic), nicméně zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je zřídka provést, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> již je výchozí chování.  
  
 Ostatní hodnoty s ekvivalentní uživatelského kódu úrovně přístupu omezení, jako například `private` v jazyce C#, nejsou důležité pro `x:ClassModifier` protože odkazy na vnořené třídy nejsou podporované v jazyce XAML a proto <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifikátor má stejný účinek.  
  
## <a name="security-notes"></a>Poznámky k zabezpečení  
 Úroveň přístupu podle údajů v `x:ClassModifier` stále podléhá interpretace konkrétní architektury a jejich funkce. WPF obsahuje funkce pro načtení a vytvoření instance typy kde `x:ClassModifier` je `internal`v případě, že třídy se odkazuje z grafického subsystému WPF prostředku prostřednictvím balíčku identifikátor URI odkazu. V důsledku tento případ a potenciálně jiné, jako je implementované ostatní platformy, nespoléhejte pouze na `x:ClassModifier` aby blokovat všechny možné konkretizaci pokusy o přihlášení.  
  
## <a name="see-also"></a>Viz také  
 [x:Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Podkladový kód a kód XAML v subsystému WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:FieldModifier – direktiva](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [Zabezpečení (WPF)](../../../docs/framework/wpf/security-wpf.md)  
 [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
