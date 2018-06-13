---
title: 'Postupy: zavedení a uvolnění sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: fe9f78e145e6b7bc8ef138ff5cdb98aa345b90c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329511"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Postupy: zavedení a uvolnění sestavení (C#)
Sestavení odkazuje vašeho programu bude automaticky načíst v čase vytvoření buildu, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu. Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Neexistuje žádný způsob, jak uvolnit jednotlivých sestavení bez uvolnění všech aplikací domén, které ji obsahují. I v případě, že sestavení ocitne mimo obor, skutečný sestavení soubor zůstane načíst, dokud se všechny domény aplikace, které ji obsahují odpojen.  
  
 Pokud chcete uvolnit některá sestavení a jiné ne, zvažte vytvoření nové domény aplikace, provádění kódu v této doméně a pak uvolnění domény aplikace. Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Načtení sestavení do domény aplikace  
  
1.  Použijte jeden z několik metod, které jsou součástí třídy načíst <xref:System.AppDomain> a <xref:System.Reflection>. Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>K uvolnění domény aplikace  
  
1.  Neexistuje žádný způsob, jak uvolnit jednotlivých sestavení bez uvolnění všech aplikací domén, které ji obsahují. Použití `Unload` metoda z <xref:System.AppDomain> uvolnění domény aplikace. Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../../csharp/programming-guide/index.md)  
 [Sestavení a globální mezipaměti sestavení (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Postupy: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
