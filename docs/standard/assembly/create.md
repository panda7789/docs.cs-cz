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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740516"
---
# <a name="create-assemblies"></a>Vytváření sestavení

Můžete vytvořit jednosouborová nebo vícesouborová sestavení pomocí ide, jako je například Visual Studio, nebo kompilátory a nástroje poskytované sadou Windows SDK. Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načten do jedné domény aplikace. Toto sestavení nelze odkazovat jinými sestaveními mimo adresář aplikace a neprochází kontrolou verze. Chcete-li odinstalovat aplikaci tvořenou sestavením, jednoduše odstraňte adresář, ve kterém je umístěn. Pro mnoho vývojářů sestavení s těmito funkcemi je vše, co je potřeba k nasazení aplikace.

Můžete vytvořit vícesouborové sestavení z několika modulů kódu a souborů prostředků. Můžete také vytvořit sestavení, které může být sdíleno více aplikacemi. Sdílené sestavení musí mít silný název a lze je nasadit v globální mezipaměti sestavení.

Máte několik možností při seskupování modulů kódu a prostředků do sestavení, v závislosti na následujících faktorech:

- Správa verzí

     Seskupit moduly, které by měly mít stejné informace o verzi.

- Nasazení

     Moduly kódu skupiny a prostředky, které podporují váš model nasazení.

- Opakované použití

     Seskupit moduly, pokud mohou být logicky použity společně pro nějaký účel. Například sestavení skládající se z typů a tříd, které se používají zřídka pro údržbu programu, může být vloženo do stejného sestavení. Kromě toho typy, které chcete sdílet s více aplikacemi by měly být seskupeny do sestavení a sestavení by měly být podepsány silným názvem.

- Zabezpečení

     Seskupte moduly obsahující typy, které vyžadují stejná oprávnění zabezpečení.

- Oboru

     Skupiny modulů obsahujících typy, jejichž viditelnost by měla být omezena na stejné sestavení.

Existují zvláštní aspekty při vytváření sestavení za běhu běžného jazyka pro nespravované aplikace COM. Další informace o práci s nespravovaným kódem naleznete v [tématu Vystavit součásti rozhraní .NET Framework modelu COM](../../framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Viz také

- [Správa verzí sestavení](versioning.md)
- [Postup: Sestavení sestavení s jedním souborem](../../framework/app-domains/build-single-file-assembly.md)
- [Postup: Sestavení vícesouborového sestavení](../../framework/app-domains/build-multifile-assembly.md)
- [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Vícesouborná sestavení](../../framework/app-domains/multifile-assemblies.md)
