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
ms.openlocfilehash: 5daff0567c1b1415fe994f6e39b4079cb2ab7346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053822"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier – direktiva
V případě, že `x:Class` je k dispozici i chování kompilace XAML, upraví. `class` Konkrétně místo vytvoření částečného, který `Public` má úroveň přístupu (výchozí nastavení), je `NotPublic` zadaný `x:Class` s úrovní přístupu. Toto chování ovlivňuje úroveň přístupu pro třídu ve vygenerovaných sestaveních.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*NotPublic*|Přesný řetězec, který se má předat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> který se liší v závislosti na programovacím jazyku na pozadí, který používáte. Viz poznámky.|  
  
## <a name="dependencies"></a>Závislosti  
 [x:Class](x-class-directive.md) musí být také zadáno na stejném elementu a tento prvek musí být kořenovým elementem na stránce. Další informace naleznete v [ \[části MS-XAML\] 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `x:ClassModifier` v .NET Framework použití služeb XAML se liší podle programovacího jazyka. Řetězec, který se má použít, závisí na tom, <xref:System.CodeDom.Compiler.CodeDomProvider> jak jednotlivé jazyky implementují své a konvertory typů, které <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> vrátí <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, aby definovali význam pro a a zda se u tohoto jazyka rozlišují malá a velká písmena.  
  
- Řetězec C#, který se má předat k určení <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , `internal`je.  
  
- Pro Microsoft Visual Basic .NET je <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`řetězec, který se má předat, označovat.  
  
- Pro C++/CLI neexistují žádné cíle, které podporují kompilaci XAML. Proto hodnota, která má být předána, není určena.  
  
 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> Můžete také zadat (`public` v C#, `Public` v Visual Basic). zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je však nečasto provedeno, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je již výchozím chováním.  
  
 Další hodnoty s ekvivalentními omezeními na `private` úrovni uživatelského kódu, jako je například v C#, nejsou relevantní `x:ClassModifier` , protože vnořené odkazy na třídy nejsou <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> v jazyce XAML podporovány, a proto má modifikátor stejný účinek. .  
  
## <a name="security-notes"></a>Poznámky k zabezpečení  
 Úroveň přístupu, jak je uvedeno `x:ClassModifier` v, je stále předmětem výkladu konkrétních platforem a jejich schopností. WPF obsahuje možnosti pro načtení a vytvoření instance typů, `x:ClassModifier` kde `internal`je, pokud je tato třída odkazována z prostředku WPF prostřednictvím odkazu identifikátoru URI balíčku. V důsledku tohoto případu a potenciálně jiným způsobem, jako je implementováno jinými rozhraními, nespoléhá výhradně na `x:ClassModifier` to, abyste zablokovali všechny možné pokusy o vytvoření instance.  
  
## <a name="see-also"></a>Viz také:

- [x:Class – direktiva](x-class-directive.md)
- [Podkladový kód a kód XAML v subsystému WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier – direktiva](x-fieldmodifier-directive.md)
- [Zabezpečení (WPF)](../wpf/security-wpf.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
