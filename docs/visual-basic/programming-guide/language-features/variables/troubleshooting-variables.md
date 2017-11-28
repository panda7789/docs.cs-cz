---
title: "Řešení potíží s proměnnými v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting [Visual Basic], variables
- variables [Visual Basic], troubleshooting
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bf6d2a0c7318c12b3001a92a8aa06625b4edabb6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-variables-in-visual-basic"></a>Řešení potíží s proměnnými v jazyce Visual Basic
Tato stránka uvádí některé běžné problémy, ke kterým dochází při práci s proměnné v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="unable-to-access-members-of-an-object"></a>Nelze přístup členům v objektu  
 Pokud váš kód pokusí o přístup k vlastnosti nebo metody objektu, existují dvě možná chyba výsledky:  
  
-   Kompilátor může vygenerovat chybovou zprávu, pokud deklarace proměnné objektu určitého typu a potom se podívejte na člena, není definována podle typu.  
  
-   Za běhu <xref:System.MemberAccessException> nastane, když je přiřazen proměnné objektu objekt nevystavuje kódu se pokouší o přístup člena. V případě proměnná [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md), můžete také získat výjimku, pokud je člen není `Public`. Důvodem je, že pozdní vazby umožňuje přístup pouze k `Public` členy.  
  
 Když [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md) kontrola typu sady `On`, proměnné objektu získat přístup pouze k metody a vlastnosti třídy, se kterým je deklarovat. Toto dokládá následující příklad.  

 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_1.vb)]  
  
 V tomto příkladu `p` můžete použít pouze členové <xref:System.Object> vlastní třídy, které nezahrnují `Left` vlastnost. Na druhé straně `q` byla deklarována jako typu <xref:System.Windows.Forms.Label>, takže můžete použít všechny metody a vlastnosti <xref:System.Windows.Forms.Label> třídy v <xref:System.Windows.Forms> oboru názvů.  
  
### <a name="correct-approach"></a>Správný přístup  
 Abyste mohli získat přístup všichni členové objektu určité třídy, deklarujte proměnnou objektu bude typu dané třídy, pokud je to možné. Pokud nelze provést, například pokud si nejste jisti, zadejte v době kompilace objekt, je nutné nastavit `Option Strict` k `Off` a deklarovat proměnnou bude [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md). To umožňuje objekty libovolného typu přiřazení proměnnou, a můžete provést kroky k zajištění, že objekt aktuálně přiřazené je přijatelné typu. Můžete použít [typeof – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) za účelem určení.  
  
## <a name="other-components-cannot-access-your-variable"></a>Ostatní součásti nelze získat přístup k vaše proměnná  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]názvy jsou *velká a malá písmena*. Pokud se liší v abecedním případě pouze dva názvy, kompilátor je interpretuje jako se stejným názvem. Například považuje `ABC` a `abc` odkazovat na stejný element deklarovaný.  
  
 Ale používá modul CLR (CLR) *malá a velká písmena* vazby. Proto při vytváření sestavení nebo knihovny DLL a zpřístupněte ho ostatních sestavení, názvy již nejsou velká a malá písmena. Například, pokud definice třídy s prvek s názvem `ABC`, a ujistěte se, ostatních sestavení pomocí vaší třídy prostřednictvím modul common language runtime, musí odkazovat na prvek jako `ABC`. Pokud následně znovu zkompiluje třídě a změňte název elementu `abc`, ostatních sestavení pomocí vlastní třídy již nebudou mít přístup tohoto prvku. Proto při uvolnění aktualizovanou verzi sestavení byste neměli měnit abecedním malá jakýchkoli veřejných složek.  
  
 Další informace najdete v tématu [modul Common Language Runtime](../../../../standard/clr.md).  
  
### <a name="correct-approach"></a>Správný přístup  
 Povolit další součásti pro přístup k proměnných, považují jejich názvy, jako kdyby byly malá a velká písmena. Při testování třídy nebo modulu, zkontrolujte, zda že ostatních sestavení vazbu s proměnnými, které očekáváte. Po publikování součást neprovádějte žádné změny existujících názvy proměnných, včetně změny jejich případech.  
  
## <a name="wrong-variable-being-used"></a>Nesprávný proměnná používá  
 Pokud máte více než jednu proměnnou se stejným názvem, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru pokusí přeložit každé odkaz na tento název. Pokud proměnné jiný rozsah, kompilátor vyřeší odkaz na deklaraci s zpomalit. Pokud mají stejný obor, řešení se nezdaří a kompilátor nevydá signál k chybě. Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
### <a name="correct-approach"></a>Správný přístup  
 Nepoužívejte proměnné se stejným názvem, ale jiný rozsah. Pokud používáte jiné sestavení nebo projekty, nepoužívejte žádné názvy definované v těchto externích součástí co nejvíc. Pokud máte více než jednu proměnnou se stejným názvem, ujistěte se, že máte nárok všechny odkazy na ni. Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Viz také  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklarace proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Postupy: přístup ke členům v objektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Hodnoty proměnné objektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Postupy: určení jaký typ proměnná objektu odkazuje](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Deklarované názvy elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
