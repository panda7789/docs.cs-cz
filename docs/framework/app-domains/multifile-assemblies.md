---
title: "Vícesouborová sestavení"
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
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bded4fae854d10a17ddd03b8855f6096e18ab87f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="multifile-assemblies"></a>Vícesouborová sestavení
Můžete vytvořit vícesouborového sestavení s využitím kompilátory příkazového řádku nebo [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] s Visual C++. Manifest sestavení musí obsahovat jeden soubor v sestavení. Sestavení, které spustí aplikaci musí také obsahovat vstupní bod, jako je například Main nebo WinMain – metoda.  
  
 Předpokládejme například, že máte aplikaci, která obsahuje dva moduly kódu, Client.cs a Stringer.cs. Vytvoří Stringer.cs `myStringer` obor názvů, který je odkazován objektem kód v Client.cs. Client.cs obsahuje `Main` metoda, která je vstupní bod aplikace. V tomto příkladu zkompilovat dva moduly kódu a pak vytvořte třetí soubor, který obsahuje manifest sestavení, který spouští aplikace. Manifest sestavení odkazuje oba `Client` a `Stringer` moduly.  
  
> [!NOTE]
>  Vícesouborová sestavení může mít pouze jeden vstupní bod, i když sestavení má více modulů kódu.  
  
 Tady je několik důvodů, které že můžete vytvořit vícesouborového sestavení:  
  
-   Kombinování moduly, které jsou napsané v různých jazycích. Toto je nejběžnější důvod pro vytváření vícesouborového sestavení.  
  
-   Chcete-li optimalizovat stahování aplikace umístěním zřídka používaný typů v modulu, který byl stažen pouze v případě potřeby.  
  
    > [!NOTE]
    >  Pokud vytváříte aplikace, které budou staženy pomocí `<object>` značky s Microsoft Internet Explorer, je důležité vytvořit vícesouborového sestavení. V tomto scénáři vytvoříte soubor odděleně od moduly kódu, které obsahuje pouze manifest sestavení. Internet Explorer nejprve stáhne manifest sestavení a pak vytvoří pracovní vlákna ke stažení všechny další moduly nebo sestavení požadovaná. Při stažení souboru, který obsahuje manifest sestavení aplikace Internet Explorer bude reagovat na vstup uživatele. Menší soubor obsahuje manifest sestavení, méně času aplikace Internet Explorer bude reagovat.  
  
-   Kombinování moduly kódu napsaných několika vývojáři. I když každý vývojář může zkompilovat každý modul kódu do sestavení, tato vynutí některé typy mají být exponovány veřejně, které nejsou vystaveny, pokud všechny moduly jsou vloženy do vícesouborového sestavení.  
  
 Jakmile vytvoříte sestavení, můžete si soubor, který obsahuje manifest sestavení (a tím i sestavení), nebo můžete poskytnout silným názvem souboru (a sestavení) a umístí jej v globální mezipaměti sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
