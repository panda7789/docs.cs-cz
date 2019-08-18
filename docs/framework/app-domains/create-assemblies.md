---
title: Vytváření sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 314a94be140b392964951299fba2fed4ac7e6e68
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566786"
---
# <a name="creating-assemblies"></a>Vytváření sestavení

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

Při zpřístupnění sestavení společného jazykového modulu runtime pro nespravované aplikace modelu COM musí být provedeny zvláštní požadavky. Další informace o práci s nespravovaným kódem najdete v tématu vystavení [.NET Framework komponent do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Viz také:

- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)
- [Postupy: Sestavení jednoho souboru sestavení](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [Postupy: Sestavení vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)
