---
title: Sestavení a souběžné spouštění
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138665"
---
# <a name="assemblies-and-side-by-side-execution"></a>Sestavení a souběžné spouštění

Souběžné spuštění je možnost ukládat a spouštět více verzí aplikace nebo součásti ve stejném počítači. To znamená, že můžete mít více verzí runtime a více verzí aplikací a součástí, které používají verzi runtime, ve stejném počítači ve stejnou dobu. Souběžné spuštění poskytuje větší kontrolu nad tím, jaké verze součásti aplikace váže, a větší kontrolu nad tím, jakou verzi runtime aplikace používá.  
  
Podpora pro souběžné úložiště a provádění různých verzí stejného sestavení je nedílnou součástí silného pojmenování a je integrována do infrastruktury runtime. Vzhledem k tomu, že číslo verze sestavení se silným názvem je součástí jeho identity, může za běhu uložit více verzí stejného sestavení do globální mezipaměti sestavení a načíst tato sestavení za běhu.  
  
Přestože runtime poskytuje možnost vytvářet souběžné aplikace, souběžné spuštění není automatické. Další informace o vytváření aplikací pro souběžné spuštění naleznete v [tématu Pokyny pro vytváření komponent pro souběžné spuštění](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Viz také

- [Jak runtime vyhledá sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Sestavení v .NET](index.md)
