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
ms.openlocfilehash: 2713011d61b41dfa4d72a635c656c0c00cb42f8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675127"
---
# <a name="creating-assemblies"></a>Vytváření sestavení

Můžete vytvořit jeden soubor nebo vícesouborové sestavení pomocí rozhraní IDE, jako je Visual Studio, nebo poskytovaný kompilátory a nástroje [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načteno do domény jednu aplikaci. Toto sestavení nemůže být odkazován jiná sestavení mimo adresář aplikace a nejdou dělit kontrolu verze. Chcete-li odinstalovat aplikaci, kterou tvoří sestavení, jednoduše odstranit adresář, ve kterém se nachází. Pro mnoho vývojářů sestavení s těmito funkcemi je vše, co je potřeba k nasazení aplikace.

Vytvořit vícesouborové sestavení z několika modulů kódu a souborů prostředků. Můžete také vytvořit sestavení, které může sdílet více aplikací. Sdílená sestavení musí mít silný název a je možné nasadit v globální mezipaměti sestavení.

Máte několik možností, jak při seskupování moduly kódu a prostředků do sestavení, v závislosti na následujících faktorech:

- Správa verzí

     Skupina modulů, které by měly mít stejné informace o verzi.

- Nasazení

     Moduly skupiny kódu a prostředků, které podporují modelu nasazení.

- Opakované použití

     Seskupit moduly, pokud jsou logicky lze společně za účelem některé. Sestavení obsahující typy a třídy zřídka používané pro údržbu programu můžete například umístit ve stejném sestavení. Kromě toho by se měly seskupit typy, které chcete sdílet s více aplikacemi do sestavení a sestavení by měl být podepsáno silným názvem.

- Zabezpečení

     Skupina moduly obsahující typy, které vyžadují stejná oprávnění zabezpečení.

- Vytváření oborů

     Skupina moduly obsahující typy, jejichž viditelnost by měla být omezena na stejné sestavení.

Speciální aspekty musí vzít v úvahu zpřístupnění common language runtime sestavení s nespravovanými aplikacemi COM. Další informace o práci s nespravovaným kódem, najdete v části [vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).

## <a name="see-also"></a>Viz také:

- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)
- [Postupy: Sestavení s jediným souborem](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)
- [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)