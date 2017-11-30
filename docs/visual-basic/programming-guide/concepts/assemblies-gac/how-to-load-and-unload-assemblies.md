---
title: "Postupy: zavedení a uvolnění sestavení (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd52a1094dba16c7e1bcba5bface9e13747cd4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a>Postupy: zavedení a uvolnění sestavení (Visual Basic)
Sestavení odkazuje vašeho programu bude automaticky načíst v čase vytvoření buildu, ale je také možné načíst konkrétní sestavení do aktuální domény aplikace za běhu. Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 Neexistuje žádný způsob, jak uvolnit jednotlivých sestavení bez uvolnění všech aplikací domén, které ji obsahují. I v případě, že sestavení ocitne mimo obor, skutečný sestavení soubor zůstane načíst, dokud se všechny domény aplikace, které ji obsahují odpojen.  
  
 Pokud chcete uvolnit některá sestavení a jiné ne, zvažte vytvoření nové domény aplikace, provádění kódu v této doméně a pak uvolnění domény aplikace. Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Načtení sestavení do domény aplikace  
  
1.  Použijte jeden z několik metod, které jsou součástí třídy načíst <xref:System.AppDomain> a <xref:System.Reflection>. Další informace najdete v tématu [postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>K uvolnění domény aplikace  
  
1.  Neexistuje žádný způsob, jak uvolnit jednotlivých sestavení bez uvolnění všech aplikací domén, které ji obsahují. Použití `Unload` metoda z <xref:System.AppDomain> uvolnění domény aplikace. Další informace najdete v tématu [postupy: uvolnění domény aplikace](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Viz také  
 [Programování konceptů](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Sestavení a globální mezipaměti sestavení (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Postupy: načtení sestavení do domény aplikace](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
