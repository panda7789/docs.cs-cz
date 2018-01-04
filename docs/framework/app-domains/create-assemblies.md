---
title: "Vytváření sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2168cbcd19437c1e275da7a01aa0c75ab47600eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-assemblies"></a>Vytváření sestavení
Můžete vytvořit jeden soubor nebo vícesouborového sestavení pomocí rozhraní IDE, jako třeba [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], nebo kompilátory a nástroje poskytované subsystémem [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Nejjednodušší sestavení je jeden soubor, který má jednoduchý název a je načteno do domény jednu aplikaci. Toto sestavení nemůže být odkazován ostatních sestavení mimo adresář aplikace a není podstoupili kontrolu verze. Pro odinstalaci aplikace skládá z sestavení, jednoduše odstranit adresář, ve kterém se nachází. Sestavení se tyto funkce pro celá řada vývojářů je všechno, co je potřeba k nasazení aplikace.  
  
 Můžete vytvořit vícesouborového sestavení z několika moduly kódu a soubory prostředků. Můžete také vytvořit sestavení, které můžete sdílet mezi více aplikacemi. Sdílené sestavení musí mít silný název a je možné nasadit v globální mezipaměti sestavení.  
  
 Máte několik možností při seskupování moduly kódu a prostředky do sestavení, a to v závislosti na následujících faktorech:  
  
-   Správa verzí  
  
     Skupiny moduly, které by měl mít stejné informace o verzi.  
  
-   Nasazení  
  
     Moduly kódu skupiny a prostředky, které podporují modelu nasazení.  
  
-   Opětovné použití  
  
     Moduly skupiny, pokud mohou být logicky použity společně pro některé účel. Například sestavení skládající se z typy a třídy používané zřídka pro Údržba programu můžou být přepnuté do stejného sestavení. Kromě toho typy, které chcete sdílet s více aplikacemi by měly být seskupené do sestavení a musí být podepsané sestavení se silným názvem.  
  
-   Zabezpečení  
  
     Skupiny moduly, který obsahuje typy, které vyžadují stejná oprávnění zabezpečení.  
  
-   Obor  
  
     Skupiny moduly obsahující typy, jejichž viditelnost by mělo být omezeno na stejné sestavení.  
  
 Při provádění common language runtime sestavení dostupné pro nespravované aplikace modelu COM, musí být provedeny zvláštní požadavky. Další informace o práci s nespravovaným kódem najdete v tématu [vystavení komponent architektury .NET Framework do modelu COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).  
  
## <a name="see-also"></a>Viz také  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Správa verzí sestavení](../../../docs/framework/app-domains/assembly-versioning.md)  
 [Postupy: Vytváření sestavení s jediným souborem](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)
