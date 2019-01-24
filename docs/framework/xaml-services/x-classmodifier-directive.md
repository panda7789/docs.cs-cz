---
title: x:ClassModifier – direktiva
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: ef55549b43ecbef539d7e84a7281fa704a328938
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507587"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier – direktiva
Upravuje chování kompilace XAML při `x:Class` je také k dispozici. Konkrétně, místo vytvoření částečné `class` , který má `Public` (výchozí) úroveň přístupu zadaných `x:Class` se vytvoří s `NotPublic` úroveň přístupu. Toto chování má vliv na úroveň přístupu pro třídu v vygenerované sestavení.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*NotPublic*|Přesná předat zadejte <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> oproti <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na použití modelu code-behind programovací jazyk, který používáte. Viz poznámky.|  
  
## <a name="dependencies"></a>Závislosti  
 [x: Class](../../../docs/framework/xaml-services/x-class-directive.md) musí se poskytnout i u stejného elementu, a tento element musí být kořenovým prvkem na stránce. Další informace najdete v tématu [ \[MS-XAML\] části 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `x:ClassModifier` v rozhraní .NET Framework XAML Services využití se liší podle programovacího jazyka. Řetězec, který má použít, závisí na způsob implementace každý jazyk jeho <xref:System.CodeDom.Compiler.CodeDomProvider> a vrátí k definování význam pro typ převaděče <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a zda je daný jazyk malá a velká písmena.  
  
-   Pro jazyk C#, řetězec, který má předat určit <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `internal`.  
  
-   Pro Microsoft Visual Basic .NET, řetězec, který má předat určit <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `Friend`.  
  
-   Pro [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], neexistují žádné cíle, které podporují kompilaci XAML; proto neurčená hodnotu pro předání.  
  
 Můžete také určit <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` v jazyce C#, `Public` v jazyce Visual Basic), nicméně zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zřídka dochází proto <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> již je výchozí chování.  
  
 Další hodnoty s ekvivalentní uživatelský kód úrovně přístupu omezení, jako například `private` v jazyce C#, nejsou relevantní pro `x:ClassModifier` protože odkazy na vnořené třídy nejsou podporovány v XAML a proto <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifikátor má stejný účinek.  
  
## <a name="security-notes"></a>Poznámky k zabezpečení  
 Úroveň přístupu, jak je deklarován v `x:ClassModifier` stále podléhá interpretaci konkrétní rozhraní a jejich funkce. WPF obsahuje funkce pro načtení a vytvoření instancí typů kde `x:ClassModifier` je `internal`, pokud tuto třídu se odkazuje z prostředku WPF prostřednictvím balíčku odkaz na identifikátor URI. Následkem tohoto případu a potenciálně ostatní jako implementované další architektury, nespoléhejte pouze na `x:ClassModifier` blokování všech možných instance pokusí.  
  
## <a name="see-also"></a>Viz také:
- [x:Class – direktiva](../../../docs/framework/xaml-services/x-class-directive.md)
- [Podkladový kód a kód XAML v subsystému WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier – direktiva](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)
- [Zabezpečení (WPF)](../../../docs/framework/wpf/security-wpf.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
