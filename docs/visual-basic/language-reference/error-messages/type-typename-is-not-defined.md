---
title: Typ &#39; &lt;typename&gt; &#39; není definován
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 8e303a9ac6529fbbc818c94497a16463897fb0c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496124"
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Typ &#39; &lt;typename&gt; &#39; není definován
Příkaz provedl odkaz na typ, který nebyl definován. Typ v příkazu deklarace můžete definovat jako `Enum`, `Structure`, `Class`, nebo `Interface`.  
  
 **ID chyby:** BC30002  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, že definice typu a jeho odkaz obou použít stejné kontroly pravopisu.  
  
-   Ujistěte se, že definice typu je přístupné pro odkaz. Například, pokud je typ v jiném modulu a byla deklarována `Private`, přesunutí definice typu pro odkazující modul nebo ji deklarovat `Public`.  
  
-   Ujistěte se, že obor názvů tohoto typu není předefinovat v rámci svého projektu. Pokud se jedná, použijte `Global` – klíčové slovo plně kvalifikovaný název typu. Například, pokud projekt definuje obor názvů s názvem `System`, <xref:System.Object?displayProperty=nameWithType> typ nelze přistupovat, pokud to není plně nekvalifikuje pomocí `Global` – klíčové slovo: `Global.System.Object`.  
  
-   Pokud je typ definován, ale není registrován objekt knihovny nebo knihovny typů, ve kterém je definována v aplikaci Visual Basic, klikněte na **přidat odkaz** na **projektu** nabídky a pak vyberte příslušný objekt Knihovna nebo knihovna typů.  
  
-   Zajistěte, aby byl typ v sestavení, která je součástí cíleném profilu rozhraní .NET. Další informace najdete v tématu [řešení chyb cílí na .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Viz také:
- [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Správa odkazů v projektu](/visualstudio/ide/managing-references-in-a-project)
