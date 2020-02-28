---
title: 'Postupy: načítání a uvolňování sestavení'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155773"
---
# <a name="how-to-load-and-unload-assemblies"></a>Postupy: načítání a uvolňování sestavení
Sestavení, na která je odkazováno pomocí programu, budou automaticky načtena modulem CLR (Common Language Runtime), ale je také možné dynamicky načíst konkrétní sestavení do aktuální domény aplikace. Další informace najdete v tématu [Postup: načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

V .NET Framework neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech domén aplikace, které ji obsahují. I v případě, že se sestavení dostane mimo rozsah, zůstane soubor vlastního sestavení načten, dokud nebudou všechny domény aplikace, které jej obsahují, uvolněny. V rozhraní .NET Core zpracovává třída <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> uvolňování sestavení. Další informace najdete v tématu [Jak používat a ladit odložení sestavení v .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Zavedení a uvolnění sestavení

Chcete-li načíst sestavení do domény aplikace, použijte jednu z několika metod načtení obsažených ve třídách <xref:System.AppDomain> a <xref:System.Reflection.Assembly>. Další informace najdete v tématu [Postup: načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Všimněte si, že .NET Core podporuje pouze jednu doménu aplikace.

Chcete-li uvolnit sestavení v .NET Framework, je nutné uvolnit všechny domény aplikace, které jej obsahují. Chcete-li uvolnit doménu aplikace, použijte metodu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>. Další informace naleznete v tématu [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).

Chcete-li uvolnit některá sestavení, ale ne jiné v aplikaci .NET Framework, zvažte vytvoření nové domény aplikace, spuštění kódu v této doméně a uvolnění této domény aplikace. Další informace naleznete v tématu [How to: Unload a Application Domain](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Viz také

- [C#Průvodce programováním](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](index.md)
- [Postupy: načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
