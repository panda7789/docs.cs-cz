---
title: 'Postupy: Načíst a uvolnit sestavení (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 3f3c244a74e029eeaead77f561cd4c1adfca519a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595835"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Postupy: Načíst a uvolnit sestavení (C#)
Sestavení, na která je odkazováno pomocí programu, budou automaticky načtena v čase sestavení, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu. Další informace najdete v tématu [jak: Načtení sestavení do domény](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikace.  
  
 Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech domén aplikace, které ji obsahují. I v případě, že se sestavení dostane mimo rozsah, zůstane soubor vlastního sestavení načten, dokud nebudou všechny domény aplikace, které jej obsahují, uvolněny.  
  
 Pokud chcete uvolnit některá sestavení, ale ne jiné, zvažte vytvoření nové domény aplikace, spuštění kódu v této doméně a následnému uvolnění této domény aplikace. Další informace najdete v tématu [jak: Uvolněte doménu](../../../../framework/app-domains/how-to-unload-an-application-domain.md)aplikace.  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Načtení sestavení do domény aplikace  
  
1. Použijte jednu z několika metod zatížení obsažených v třídách <xref:System.AppDomain> a. <xref:System.Reflection> Další informace najdete v tématu [jak: Načtení sestavení do domény](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)aplikace.  
  
### <a name="to-unload-an-application-domain"></a>Uvolnění domény aplikace  
  
1. Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech domén aplikace, které ji obsahují. Použijte metodu z <xref:System.AppDomain> k uvolnění aplikačních domén. `Unload` Další informace najdete v tématu [jak: Uvolněte doménu](../../../../framework/app-domains/how-to-unload-an-application-domain.md)aplikace.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../index.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Postupy: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
