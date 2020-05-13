---
title: 'Postupy: načítání a uvolňování sestavení'
description: Modul CLR automaticky načte sestavení .NET, na která odkazuje program. Můžete také dynamicky načíst konkrétní sestavení do aktuální domény aplikace.
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: e6f1ede055dd3f68bced4eba527b2fc65f7d5715
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378685"
---
# <a name="how-to-load-and-unload-assemblies"></a>Postupy: načítání a uvolňování sestavení
Sestavení, na která je odkazováno pomocí programu, budou automaticky načtena modulem CLR (Common Language Runtime), ale je také možné dynamicky načíst konkrétní sestavení do aktuální domény aplikace. Další informace najdete v tématu [Postup: načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

V .NET Framework neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech domén aplikace, které ji obsahují. I v případě, že se sestavení dostane mimo rozsah, zůstane soubor vlastního sestavení načten, dokud nebudou všechny domény aplikace, které jej obsahují, uvolněny. V .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> Třída zpracovává uvolňování sestavení. Další informace najdete v tématu [Jak používat a ladit odložení sestavení v .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Zavedení a uvolnění sestavení

Chcete-li načíst sestavení do domény aplikace, použijte jednu z několika metod zatížení obsažených v třídách <xref:System.AppDomain> a <xref:System.Reflection.Assembly> . Další informace najdete v tématu [Postup: načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Všimněte si, že .NET Core podporuje pouze jednu doménu aplikace.

Chcete-li uvolnit sestavení v .NET Framework, je nutné uvolnit všechny domény aplikace, které jej obsahují. Chcete-li uvolnit doménu aplikace, použijte <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metodu. Další informace naleznete v tématu [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).

Chcete-li uvolnit některá sestavení, ale ne jiné v aplikaci .NET Framework, zvažte vytvoření nové domény aplikace, spuštění kódu v této doméně a uvolnění této domény aplikace. Další informace naleznete v tématu [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](index.md)
- [Postupy: načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
