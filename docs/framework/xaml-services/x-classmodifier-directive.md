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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837230"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier – direktiva
Upravuje chování kompilace XAML, pokud je k dispozici také `x:Class`. Konkrétně místo vytvoření částečného `class`, který má úroveň přístupu `Public` (výchozí nastavení), je zadaný `x:Class` vytvořen s úrovní přístupu `NotPublic`. Toto chování ovlivňuje úroveň přístupu pro třídu ve vygenerovaných sestaveních.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*NotPublic*|Přesný řetězec, který má být předána <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na programovacím jazyku na pozadí, který používáte. Viz poznámky.|  
  
## <a name="dependencies"></a>Závislosti  
 [x:Class](x-class-directive.md) musí být také zadáno na stejném elementu a tento prvek musí být kořenovým elementem na stránce. Další informace naleznete v tématu [\[MS-XAML\] oddílu 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `x:ClassModifier` v .NET Framework použití služeb XAML se liší podle programovacího jazyka. Řetězec, který se má použít, závisí na tom, jak jednotlivé jazyky implementují své <xref:System.CodeDom.Compiler.CodeDomProvider> a převaděče typu, které vrátí, aby definovali význam pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>a zda se u tohoto jazyka rozlišují malá a velká písmena.  
  
- Řetězec C#, který se má předat určit <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, je `internal`.  
  
- Pro Microsoft Visual Basic .NET je řetězec, který se má předat, označit jako <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`.  
  
- Pro C++/CLI neexistují žádné cíle, které podporují kompilaci XAML. Proto hodnota, která má být předána, není určena.  
  
 Můžete také zadat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` v C#`Public` v Visual Basic); určení <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> však není často prováděno, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je již výchozím chováním.  
  
 Jiné hodnoty s ekvivalentními omezeními na úrovni uživatelského kódu, jako je například C#`private` v, nejsou relevantní pro `x:ClassModifier`, protože vnořené odkazy na třídy nejsou v jazyce XAML podporovány a proto má modifikátor <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> stejný účinek.  
  
## <a name="security-notes"></a>Poznámky k zabezpečení  
 Úroveň přístupu deklarovaná v `x:ClassModifier` stále podléhá výkladu konkrétními rozhraními a jejich schopnostmi. WPF obsahuje možnosti pro načtení a vytvoření instance typů, kde `x:ClassModifier` je `internal`, pokud je tato třída odkazována z prostředku WPF prostřednictvím odkazu na identifikátor URI balíčku. Jako důsledek tohoto případu a potenciálně jiné, jako je implementováno jinými rozhraními, nespoléhá výhradně na `x:ClassModifier` k blokování všech možných pokusů o vytvoření instance.  
  
## <a name="see-also"></a>Viz také:

- [x:Class – direktiva](x-class-directive.md)
- [Podkladový kód a kód XAML v subsystému WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier – direktiva](x-fieldmodifier-directive.md)
- [Zabezpečení (WPF)](../wpf/security-wpf.md)
- [Typy migrované z prostředí WPF do oboru názvů System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
