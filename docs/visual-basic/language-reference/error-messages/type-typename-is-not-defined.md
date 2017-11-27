---
title: "Typ & č. 39; &lt;typename&gt;& č. 39; není definován"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords: BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Typ & č. 39; &lt;typename&gt;& č. 39; není definován
Příkaz provedl odkaz na typ, který nebyl definován. Typ v deklaraci příkazu můžete definovat jako `Enum`, `Structure`, `Class`, nebo `Interface`.  
  
 **ID chyby:** BC30002  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte, jestli definici typu a jeho referenční obě používají stejné pravopis.  
  
-   Ujistěte se, že je dostupný pro odkaz na definici tohoto typu. Například, pokud je v jiném modulu typu a bylo deklarováno `Private`, přesuňte definici typu modulu odkazující nebo deklarujte ji `Public`.  
  
-   Ujistěte se, že není v rámci projektu předefinovat obor názvů typu. Pokud je, použijte `Global` – klíčové slovo plně kvalifikovaný název typu. Například pokud projektu definuje obor názvů s názvem `System`, <xref:System.Object?displayProperty=nameWithType> typ nelze přistupovat, pokud je plně kvalifikovaný s `Global` – klíčové slovo: `Global.System.Object`.  
  
-   Pokud je definován typ, ale není registrován objekt knihovny nebo knihovny typů, ve kterém je definovaný v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], klikněte na tlačítko **přidat odkaz na** na **projektu** nabídce a pak vyberte příslušný objekt Knihovna nebo knihovny typů.  
  
-   Ujistěte se, že typ je v sestavení, které je součástí profilu cílové rozhraní .NET Framework. Další informace najdete v tématu [řešení potíží s chybami cílení na rozhraní .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Viz také  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
