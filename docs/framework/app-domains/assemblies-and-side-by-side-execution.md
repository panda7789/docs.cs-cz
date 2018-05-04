---
title: Sestavení a souběžné spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 605cb6dfd3232d90d6c278f9563ac8d9f101b053
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="assemblies-and-side-by-side-execution"></a>Sestavení a souběžné spouštění
Souběžného zpracování se možnost ukládat a spouštět více verzí aplikace nebo součásti na stejném počítači. To znamená, že můžete mít více verzí modulu runtime a více verzí aplikací a součástí, které používají verzi modulu runtime na stejném počítači ve stejnou dobu. Souběžně sdílená spouštění vám dává větší kontrolu nad jaké verze komponenty jsou svázány s aplikací a větší kontrolu nad jaká verze modulu runtime aplikace používá.  
  
 Podpora pro úložiště vedle sebe a provádění různých verzí stejného sestavení je nedílnou součástí silné názvy a je integrovaná do infrastrukturu modulu runtime. Číslo verze sestavení silným názvem je součástí svoji identitu, modul runtime můžete uložit více verzí stejného sestavení v globální mezipaměti sestavení a načtení těchto sestavení za běhu.  
  
 I když se modul runtime poskytuje schopnost vytvářet aplikace vedle sebe, není automatické spuštění vedle sebe. Další informace o vytváření aplikací pro spuštění vedle sebe najdete v tématu [pokyny pro vytváření komponent pro spuštění vedle sebe](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Viz také  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
