---
title: 'Postup: Načtení a uvolnění sestavení'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155773"
---
# <a name="how-to-load-and-unload-assemblies"></a>Postup: Načtení a uvolnění sestavení
Sestavení, na která program odkazuje, budou automaticky načtena běžným jazykem runtime, ale je také možné dynamicky načítat konkrétní sestavení do aktuální domény aplikace. Další informace naleznete v [tématu How to: Load assemblies into a application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

V rozhraní .NET Framework neexistuje žádný způsob, jak uvolnit jednotlivé sestavení bez uvolnění všech aplikačních domén, které jej obsahují. I v případě, že sestavení přejde mimo rozsah, skutečný soubor sestavení zůstane načten, dokud nebudou uvolněny všechny aplikační domény, které jej obsahují. V .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> třída zpracovává uvolnění sestavení. Další informace naleznete [v tématu Použití a ladění použitelnosti sestavení v .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Zavedení a uvolnění sestavení

Chcete-li načíst sestavení do domény aplikace, použijte jednu <xref:System.AppDomain> z <xref:System.Reflection.Assembly>několika metod zatížení obsažených ve třídách a . Další informace naleznete v [tématu How to: Load assemblies into a application domain](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Všimněte si, že rozhraní .NET Core podporuje pouze jednu doménu aplikace.

Chcete-li uvolnit sestavení v rozhraní .NET Framework, musíte uvolnit všechny aplikační domény, které jej obsahují. Chcete-li uvolnit doménu <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> aplikace, použijte metodu. Další informace naleznete v [tématu How to: Unload a application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).

Pokud chcete uvolnit některá sestavení, ale ne jiná v aplikaci rozhraní .NET Framework, zvažte vytvoření nové domény aplikace, spuštění kódu uvnitř této domény a uvolnění této domény aplikace. Další informace naleznete v [tématu How to: Unload a application domain](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../../csharp/programming-guide/index.md)
- [Koncepty programování (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](index.md)
- [Postup: Načtení sestavení do domény aplikace](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
