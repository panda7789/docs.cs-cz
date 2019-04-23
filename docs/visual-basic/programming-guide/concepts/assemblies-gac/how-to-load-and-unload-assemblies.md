---
title: 'Postupy: Zavedení a uvolnění sestavení (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
ms.openlocfilehash: efd8ddbe45323e1f80cec54379d61b5aa8a435cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297380"
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Postupy: Zavedení a uvolnění sestavení (Visual Basic)
Sestavení odkazuje váš program bude automaticky načtených v okamžiku sestavení, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu. Další informace najdete v tématu [jak: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují. I v případě, sestavení dostane mimo rozsah, zůstane soubor skutečné sestavení načteno, dokud jsou uvolněna, všechny aplikační domény, které obsahují.  
  
 Pokud chcete uvolnit, některá sestavení, ale ne pro jiné, zvažte vytvoření nové aplikační doméně, spouštění kódu v této doméně a pak uvolnění této domény aplikace. Další informace najdete v tématu [jak: Uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Načtení sestavení do domény aplikace  
  
1. Použijte jednu z několik načíst metody obsažené v třídách <xref:System.AppDomain> a <xref:System.Reflection>. Další informace najdete v tématu [jak: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>K uvolnění domény aplikace  
  
1. Neexistuje žádný způsob, jak uvolnit jednotlivá sestavení bez uvolnění všech aplikačních domén, které je obsahují. Použití `Unload` metodu z <xref:System.AppDomain> uvolnění domény aplikace. Další informace najdete v tématu [jak: Uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Viz také:

- [Koncepty programování](../../../../visual-basic/programming-guide/concepts/index.md)
- [Sestavení v .NET](../../../../standard/assembly/index.md)
- [Postupy: Načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
