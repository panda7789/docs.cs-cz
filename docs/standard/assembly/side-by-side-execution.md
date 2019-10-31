---
title: Sestavení a souběžné spouštění
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138665"
---
# <a name="assemblies-and-side-by-side-execution"></a>Sestavení a souběžné spouštění

Souběžné spouštění je schopnost ukládat a spouštět více verzí aplikace nebo komponenty na stejném počítači. To znamená, že můžete mít více verzí modulu runtime a více verzí aplikací a komponent, které používají verzi modulu runtime, ve stejném počítači současně. Souběžné spouštění nabízí větší kontrolu nad tím, na které verze komponenty se aplikace váže, a lepší kontrolu nad tím, jakou verzi modulu runtime aplikace používá.  
  
Podpora pro souběžné ukládání a provádění různých verzí stejného sestavení je nedílnou součástí silného pojmenování a je integrována do infrastruktury modulu runtime. Vzhledem k tomu, že číslo verze sestavení se silným názvem je součástí své identity, modul runtime může uložit více verzí stejného sestavení v globální mezipaměti sestavení (GAC) a načíst tato sestavení za běhu.  
  
I když modul runtime poskytuje možnost vytvářet souběžné aplikace, nejedná se o automatické spuštění souběžného spouštění. Další informace o vytváření aplikací pro souběžné spouštění najdete v tématu [pokyny pro vytváření komponent pro souběžné spouštění](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Viz také:

- [Způsob, jakým modul runtime vyhledává sestavení](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Sestavení v .NET](index.md)
