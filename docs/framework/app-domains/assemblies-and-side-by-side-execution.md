---
title: Sestavení a souběžné spouštění
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa44090e589e7a2a70b8fb7dbd8d5e6967c1ed19
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126633"
---
# <a name="assemblies-and-side-by-side-execution"></a>Sestavení a souběžné spouštění
Vedle sebe spuštění je schopnost ukládat a spouštět více verzí aplikace nebo komponenty na stejném počítači. To znamená, že můžete mít více verzí modulu runtime a více verzí aplikací a komponent, které používají verzi modulu runtime, ve stejném počítači ve stejnou dobu. Vedle sebe spouštění dává větší kontrolu nad jakou verzí komponenty je aplikace propojena, a mít větší kontrolu nad jakou verzi modulu runtime aplikace používá.  
  
 Podpora úložiště vedle sebe a provádění různých verzí stejného sestavení je nedílnou součástí silné názvy a je součástí infrastruktury modulu runtime. Protože číslo verze sestavení silným názvem je součástí svoji identitu, modul runtime lze uložit více verzí stejného sestavení v globální mezipaměti sestavení a načtení těchto sestavení v době běhu.  
  
 I když se modul runtime poskytuje možnost vytvářet aplikace vedle sebe, není automatická spuštění vedle sebe. Další informace o vytváření aplikací pro spuštění vedle sebe, naleznete v tématu [pokyny pro vytváření komponent pro spuštění vedle sebe](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Viz také:

- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Sestavení v modulu CLR (Common Language Runtime)](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
