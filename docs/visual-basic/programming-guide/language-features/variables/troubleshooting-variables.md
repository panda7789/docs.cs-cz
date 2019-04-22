---
title: Řešení potíží s proměnnými v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
ms.openlocfilehash: 55d0fdcdbed4f994e50e83e5a25baf83c3ad79cc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831121"
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Řešení potíží s proměnnými v jazyce Visual Basic
Tato stránka obsahuje některé běžné problémy, které se mohou vyskytnout při práci s proměnnými v jazyce Visual Basic.  
  
## <a name="unable-to-access-members-of-an-object"></a>Nelze získat přístup ke členům objektu  
 Pokud váš kód se pokusí získat přístup k vlastnosti nebo metody pro objekt, existují dvě možná chyba výsledků:  
  
-   Kompilátor může generovat chybovou zprávu, pokud deklarujete proměnnou objektu určitého typu a přečtěte si informace na člen nejsou definovány parametrem typu.  
  
-   Za běhu <xref:System.MemberAccessException> nastane, pokud objekt přiřazen do proměnné objektu nevystavuje člen váš kód se pokouší o přístup. V případě proměnné [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md), můžete také získat tuto výjimku, pokud člen není `Public`. Důvodem je, že pozdní vazby povolí přístup pouze k `Public` členy.  
  
 Když [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kontrolu typů sad `On`, proměnné objektu přístupné pouze metody a vlastnosti třídy, se kterým se deklaruje. Toto dokládá následující příklad.  

 [!code-vb[VbVbalrVariables#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#2)]  
  
 V tomto příkladu `p` lze použít pouze členové <xref:System.Object> třídu, která nejsou zahrnuté `Left` vlastnost. Na druhé straně `q` byl deklarován jako typ <xref:System.Windows.Forms.Label>, takže ho můžete použít všechny metody a vlastnosti <xref:System.Windows.Forms.Label> třídy v <xref:System.Windows.Forms> oboru názvů.  
  
### <a name="correct-approach"></a>Správný přístup  
 Aby bylo možné pro přístup ke členům objektu určité třídy, deklarace proměnné objektu typu dané třídy, pokud je to možné. Pokud nelze toto provedete, například pokud si nejste jisti objektu typu v době kompilace, je nutné nastavit `Option Strict` k `Off` a deklarovat proměnnou, bude [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md). To umožňuje objektů libovolného typu, který má být přiřazena k proměnné a byste měli podniknout kroky k ověření, že aktuálně přiřazené objektu je přijatelné typu. Můžete použít [TypeOf operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) za účelem určení.  
  
## <a name="other-components-cannot-access-your-variable"></a>Ostatní součásti nelze přistupovat k proměnné  
 Názvy jazyka Visual Basic jsou *velkých a malých písmen*. Pokud se dva názvy liší abecední pouze velikostí písmen, je kompilátor interpretuje jako se stejným názvem. Například považuje `ABC` a `abc` odkazovat na stejný element deklarovaný.  
  
 Nicméně, používá modul CLR (CLR) *malá a velká písmena* vazby. Proto se při vytvoření sestavení nebo knihovny DLL a ji dejte k dispozici pro jiná sestavení, názvy už nejsou velká a malá písmena. Například pokud definujete třídu s názvem elementu `ABC`, a jiných sestavení pomocí třídy přes modul common language runtime, musí odkazovat na prvek jako `ABC`. Pokud následně znovu zkompilovat vaší třídy a změňte název elementu na `abc`, ostatních sestavení pomocí vaší třídy už mít přístup k prvku. Proto při uvolnění aktualizovanou verzi sestavení, byste neměli měnit abecední případ veřejné elementy.  
  
 Další informace najdete v tématu [Common Language Runtime](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Správný přístup  
 Povolit další komponenty pro přístup k proměnných, nakládat s jejich názvy, jako by byly malá a velká písmena. Při testování třídu nebo modul, zkontrolujte, zda že jiná sestavení vazbu k proměnné, které očekáváte. Po publikování komponenty neprovádějte žádné změny existujících názvy proměnných, včetně změny jejich případy.  
  
## <a name="wrong-variable-being-used"></a>Chybný používá proměnné  
 Pokud máte více než jednu proměnnou se stejným názvem, kompilátor jazyka Visual Basic se pokusí přeložit každé odkaz na tento název. Pokud proměnné jiného oboru, přeloží kompilátor odkaz na prohlášení s zpomalit. Pokud mají stejný obor, na řešení se nezdaří a kompilátor signály chybu. Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Správný přístup  
 Vyhněte se použití proměnné se stejným názvem, ale jiného oboru. Pokud používáte jiné projekty nebo sestavení, nepoužívejte názvy definované v těchto externích komponent co největší míře. Pokud máte více než jednu proměnnou se stejným názvem, ujistěte se, že kvalifikovat všechny odkazy na ni. Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Viz také:

- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Deklarace objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Postupy: Přístup k členům v objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Postupy: Určit, jaký typ proměnná objektu odkazuje](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
