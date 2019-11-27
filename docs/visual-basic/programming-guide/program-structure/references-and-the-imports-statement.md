---
title: Odkazy a příkaz Imports
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 31b4fe001f2b8a62ac30488053c57cd186020421
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347278"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Odkazy a příkaz Imports (Visual Basic)
Můžete zpřístupnit externí objekty projektu výběrem příkazu **Přidat odkaz** v nabídce **projekt** . Odkazy v Visual Basic mohou odkazovat na sestavení, která jsou jako knihovny typů, ale obsahují více informací.  
  
## <a name="the-imports-statement"></a>Příkaz Imports  
 Sestavení zahrnují jeden nebo více oborů názvů. Přidáte-li odkaz na sestavení, můžete také přidat příkaz `Imports` do modulu, který řídí viditelnost oborů názvů tohoto sestavení v rámci modulu. Příkaz `Imports` poskytuje obor kontextu, který umožňuje používat pouze část oboru názvů, který je nezbytný k poskytnutí jedinečného odkazu.  
  
 Příkaz `Imports` má následující syntaxi:  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname` odkazuje na krátký název, který můžete použít v rámci kódu pro odkazování na importovaný obor názvů. `Namespace` je obor názvů dostupný buď prostřednictvím odkazu na projekt, prostřednictvím definice v rámci projektu, nebo prostřednictvím předchozího příkazu `Imports`.  
  
 Modul může obsahovat libovolný počet příkazů `Imports`. Musí se objevit za jakýmkoli `Option`mi příkazy, pokud jsou přítomny, ale před jakýmkoli jiným kódem.  
  
> [!NOTE]
> Nezaměňujte odkazy na projekt pomocí příkazu `Imports` nebo příkazu `Declare`. Odkazy na projekt zpřístupňují externí objekty, například objekty v sestaveních, k dispozici pro Visual Basic projekty. Příkaz `Imports` slouží k zjednodušení přístupu k projektovým odkazům, ale neposkytuje přístup k těmto objektům. Příkaz `Declare` slouží k deklaraci odkazu na externí proceduru v dynamické knihovně (DLL).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Použití aliasů s příkazem Imports  
 Příkaz `Imports` usnadňuje přístup k metodám tříd tím, že eliminuje nutnost explicitně zadat plně kvalifikované názvy odkazů. Aliasy umožňují přiřadit název příjemnější pouze jedné části oboru názvů. Například sekvence návratového a řádkového kanálu, která způsobuje, že se na více řádcích zobrazí jedna část textu, je součástí modulu <xref:Microsoft.VisualBasic.ControlChars> v oboru názvů <xref:Microsoft.VisualBasic?displayProperty=nameWithType>. Chcete-li použít tuto konstantu v programu bez aliasu, je třeba zadat následující kód:  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 příkazy `Imports` musí být vždy první řádky hned za všemi příkazy `Option` v modulu. Následující fragment kódu ukazuje, jak importovat a přiřadit alias k modulu <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>:  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 Budoucí odkazy na tento obor názvů můžou být výrazně kratší:  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 Pokud příkaz `Imports` nezahrnuje název aliasu, prvky definované v rámci importovaného oboru názvů lze v modulu použít bez kvalifikace. Pokud je název aliasu zadán, je nutné jej použít jako kvalifikátor názvů obsažených v daném oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Obory názvů v Visual Basic](namespaces.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
