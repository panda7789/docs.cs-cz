---
title: Typ &#39; &lt;typename&gt; &#39; není definován
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 20f36a06000d0197ad80b83766f6612a474d5758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595183"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Typ &#39; &lt;typename&gt; &#39; není definován
Příkaz provedl odkaz na typ, který nebyl definován. Typ v deklaraci příkazu můžete definovat jako `Enum`, `Structure`, `Class`, nebo `Interface`.  
  
 **ID chyby:** BC30002  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte, jestli definici typu a jeho referenční obě používají stejné pravopis.  
  
-   Ujistěte se, že je dostupný pro odkaz na definici tohoto typu. Například, pokud je v jiném modulu typu a bylo deklarováno `Private`, přesuňte definici typu modulu odkazující nebo deklarujte ji `Public`.  
  
-   Ujistěte se, že není v rámci projektu předefinovat obor názvů typu. Pokud je, použijte `Global` – klíčové slovo plně kvalifikovaný název typu. Například pokud projektu definuje obor názvů s názvem `System`, <xref:System.Object?displayProperty=nameWithType> typ nelze přistupovat, pokud je plně kvalifikovaný s `Global` – klíčové slovo: `Global.System.Object`.  
  
-   Pokud je definován typ, ale není registrován objekt knihovny nebo knihovny typů, ve kterém je definovaný v Visual Basic, klikněte na tlačítko **přidat odkaz na** na **projektu** nabídce a pak vyberte příslušný objekt Knihovna nebo knihovny typů.  
  
-   Ujistěte se, že typ je v sestavení, které je součástí profilu cílové rozhraní .NET Framework. Další informace najdete v tématu [řešení potíží s chybami cílení na rozhraní .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Viz také  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
