---
title: 'Postupy: Načíst a uvolnit sestavení'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973199"
---
# <a name="how-to-load-and-unload-assemblies"></a>Postupy: Načíst a uvolnit sestavení
Sestavení, na která je odkazováno pomocí programu, budou automaticky načtena modulem CLR (Common Language Runtime), ale je také možné dynamicky načíst konkrétní sestavení do aktuální domény aplikace. Další informace najdete v tématu [jak: Načtení sestavení do domény](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikace.

V .NET Framework neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech domén aplikace, které ji obsahují. I v případě, že se sestavení dostane mimo rozsah, zůstane soubor vlastního sestavení načten, dokud nebudou všechny domény aplikace, které jej obsahují, uvolněny. V .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> třída zpracovává uvolňování sestavení. Další informace najdete v tématu [Jak používat a ladit odložení sestavení v .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Načíst a uvolnit sestavení

Chcete-li načíst sestavení do domény aplikace, použijte jednu z několika metod zatížení obsažených v třídách <xref:System.AppDomain> a. <xref:System.Reflection.Assembly> Další informace najdete v tématu [jak: Načtení sestavení do domény](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikace. Všimněte si, že .NET Core podporuje pouze jednu doménu aplikace. 

Chcete-li uvolnit sestavení v .NET Framework, je nutné uvolnit všechny domény aplikace, které jej obsahují. Chcete-li uvolnit doménu aplikace, použijte <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metodu. Další informace najdete v tématu [jak: Uvolněte doménu](../../framework/app-domains/how-to-unload-an-application-domain.md)aplikace.

Chcete-li uvolnit některá sestavení, ale ne jiné v aplikaci .NET Framework, zvažte vytvoření nové domény aplikace, spuštění kódu v této doméně a uvolnění této domény aplikace. Další informace najdete v tématu [jak: Uvolněte doménu](../../framework/app-domains/how-to-unload-an-application-domain.md)aplikace.  

## <a name="see-also"></a>Viz také:

- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](index.md)
- [Postupy: Načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
