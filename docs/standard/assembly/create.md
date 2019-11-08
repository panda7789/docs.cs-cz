---
title: Vytváření sestavení
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 81fffb2b2e1d56d6068bf6f663a13fad6968a383
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740516"
---
# <a name="create-assemblies"></a>Vytváření sestavení

Můžete vytvořit jednosouborové nebo vícesouborové sestavení pomocí integrovaného vývojového prostředí (IDE), jako je například Visual Studio, nebo kompilátorů a nástrojů poskytovaných Windows SDK. Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načten do jedné domény aplikace. Na toto sestavení nemůže odkazovat jiná sestavení mimo adresář aplikace a neprovádí kontrolu verze. Chcete-li odinstalovat aplikaci tvořenou sestavením, stačí odstranit adresář, ve kterém se nachází. Pro mnoho vývojářů je sestavení s těmito funkcemi všechno, co je potřeba k nasazení aplikace.

Můžete vytvořit vícesouborové sestavení z několika modulů kódu a souborů prostředků. Můžete také vytvořit sestavení, které může být sdíleno více aplikacemi. Sdílené sestavení musí mít silný název a může být nasazeno v globální mezipaměti sestavení (GAC).

Máte několik možností, jak seskupit moduly kódu a prostředky do sestavení, v závislosti na následujících faktorech:

- Správa verzí

     Seskupujte moduly, které by měly mít stejné informace o verzi.

- Nasazení

     Seskupuje moduly a prostředky kódu, které podporují váš model nasazení.

- Opakovan

     Skupinové moduly, pokud je lze logicky používat pro určitý účel. Například sestavení sestávající z typů a tříd, které jsou používány zřídka pro údržbu programu, lze umístit do stejného sestavení. Kromě toho musí být typy, které chcete sdílet s více aplikacemi, seskupeny do sestavení a sestavení by mělo být podepsáno silným názvem.

- Zabezpečení

     Moduly skupin obsahující typy, které vyžadují stejná oprávnění zabezpečení.

- Rozsah

     Moduly skupin obsahující typy, jejichž viditelnost by měly být omezeny na stejné sestavení.

Existují zvláštní předpoklady pro zpřístupnění sestavení společného jazykového modulu runtime pro nespravované aplikace modelu COM. Další informace o práci s nespravovaným kódem naleznete v tématu [Vystavení .NET Frameworkch komponent modelu COM](../../framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Viz také:

- [Správa verzí sestavení](versioning.md)
- [Postupy: sestavení sestavení s jedním souborem](../../framework/app-domains/build-single-file-assembly.md)
- [Postupy: sestavení vícesouborového sestavení](../../framework/app-domains/build-multifile-assembly.md)
- [Způsob, jakým modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Vícesouborové sestavení](../../framework/app-domains/multifile-assemblies.md)
