---
title: Odkazy a příkaz Imports (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
ms.openlocfilehash: 5b810af86f8659ffbe27d23d36aece408516a9bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972049"
---
# <a name="references-and-the-imports-statement-visual-basic"></a>Odkazy a příkaz Imports (Visual Basic)
Můžete zpřístupnit externí objekty projektu výběrem příkazu **Přidat odkaz** v nabídce **projekt** . Odkazy v Visual Basic mohou odkazovat na sestavení, která jsou jako knihovny typů, ale obsahují více informací.  
  
## <a name="the-imports-statement"></a>Příkaz Imports  
 Sestavení zahrnují jeden nebo více oborů názvů. Když přidáte odkaz na sestavení, můžete také přidat `Imports` příkaz do modulu, který ovládá viditelnost oborů názvů tohoto sestavení v rámci modulu. `Imports` Příkaz poskytuje obor kontextu, který umožňuje používat pouze část oboru názvů, který je nezbytný k poskytnutí jedinečného odkazu.  
  
 `Imports` Příkaz má následující syntaxi:  
  
 `Imports [Aliasname =] Namespace`  
  
 `Aliasname`odkazuje na krátký název, který lze použít v rámci kódu pro odkazování na importovaný obor názvů. `Namespace`je obor názvů dostupný prostřednictvím odkazu na projekt, prostřednictvím definice v rámci projektu nebo prostřednictvím předchozího `Imports` příkazu.  
  
 Modul může obsahovat libovolný počet `Imports` příkazů. Musí se vyskytovat po všech `Option` příkazech, pokud jsou přítomny, ale před jakýmkoli jiným kódem.  
  
> [!NOTE]
> Nezaměňujte odkazy na projekt pomocí `Imports` příkazu `Declare` nebo příkazu. Odkazy na projekt zpřístupňují externí objekty, například objekty v sestaveních, k dispozici pro Visual Basic projekty. `Imports` Příkaz slouží k zjednodušení přístupu k odkazům na projekt, ale neposkytuje přístup k těmto objektům. `Declare` Příkaz se používá k deklaraci odkazu na externí proceduru v knihovně DLL (Dynamic-Link Library).  
  
## <a name="using-aliases-with-the-imports-statement"></a>Použití aliasů s příkazem Imports  
 `Imports` Příkaz usnadňuje přístup k metodám tříd tím, že eliminuje nutnost explicitně zadat plně kvalifikované názvy odkazů. Aliasy umožňují přiřadit název příjemnější pouze jedné části oboru názvů. Například sekvence návratového a řádkového kanálu, která způsobuje, že se na více řádcích zobrazí jedna část textu, je součástí <xref:Microsoft.VisualBasic.ControlChars> modulu <xref:Microsoft.VisualBasic?displayProperty=nameWithType> v oboru názvů. Chcete-li použít tuto konstantu v programu bez aliasu, je třeba zadat následující kód:  
  
 [!code-vb[VbVbalrApplication#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#3)]  
  
 `Imports`příkazy musí být vždy první řádky hned za všemi `Option` příkazy v modulu. Následující fragment kódu ukazuje, jak importovat a přiřadit k <xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType> modulu alias:  
  
 [!code-vb[VbVbalrApplication#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#4)]  
  
 Budoucí odkazy na tento obor názvů můžou být výrazně kratší:  
  
 [!code-vb[VbVbalrApplication#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#5)]  
  
 `Imports` Pokud příkaz neobsahuje název aliasu, prvky definované v rámci importovaného oboru názvů lze v modulu použít bez kvalifikace. Pokud je název aliasu zadán, je nutné jej použít jako kvalifikátor názvů obsažených v daném oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ControlChars>
- <xref:Microsoft.VisualBasic>
- [Obory názvů v Visual Basic](namespaces.md)
- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Příkaz Imports (obor názvů a typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
