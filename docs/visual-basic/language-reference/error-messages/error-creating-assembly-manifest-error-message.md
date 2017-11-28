---
title: "Chyba při vytváření sestavení manifestu: &lt;chybová zpráva&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Chyba při vytváření sestavení manifestu: &lt;chybová zpráva&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilátoru volá Linker sestavení (Al.exe, také známé jako Alink) ke generování sestavení s manifestu. Linkeru ohlásilo chybu ve fázi před emisí vytváření sestavení.  
  
 Tato situace může nastat, pokud dochází k problémům s souboru klíče nebo klíče zadaný kontejner. Chcete-li plně podepsání sestavení, je nutné zadat platný soubor klíče, který obsahuje informace o veřejné a soukromé klíče. Zpoždění podepsání sestavení, musíte vybrat **zpoždění podepsání** zaškrtněte políčko a zadejte platný soubor klíče, který obsahuje informace o informace o veřejném klíči. Privátní klíč není nutné, pokud je sestavení podepsané zpoždění. Další informace najdete v tématu [postupy: podepsání sestavení (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **ID chyby:** BC30140  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Prověřením uvozovkách chybové zprávy a podívejte se téma [Nástroj Al.exe chyby a upozornění](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) došlo k chybě AL1019 další vysvětlení a Rady, jak  
  
2.  Pokud potíže potrvají, shromažďovat informace o okolnostech a upozornění služby Microsoft Product Support Services.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: podepsání sestavení (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [Stránka podepisování, Návrhář projektu](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe (Linker sestavení)](https://msdn.microsoft.com/library/c405shex)  
 [Al.exe nástroj chyby a upozornění](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [Kontaktujte nás](/visualstudio/ide/talk-to-us)
