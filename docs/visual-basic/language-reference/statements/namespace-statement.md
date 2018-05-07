---
title: Namespace – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: 15d8d8185d895502df594bbd931443af604bef67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="namespace-statement"></a>Namespace – příkaz
Deklaruje název oboru názvů a způsobí, že zdrojový kód, který odpovídá deklaraci sestavují v daném oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Součásti  
 Globální  
 Volitelné. Můžete zadat obor názvů z kořenového oboru názvů vašeho projektu. V tématu [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Požadováno. Jedinečný název, který identifikuje obor názvů. Musí být platný identifikátor jazyka Visual Basic. Další informace najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Volitelné. Prvky, které tvoří obor názvů. Ty zahrnují, ale nejsou omezeny na výčty, struktury, rozhraní, třídy, moduly, delegáti a jiných oborech názvů.  
  
 `End Namespace`  
 Ukončí `Namespace` bloku.  
  
## <a name="remarks"></a>Poznámky  
 Obory názvů se používají jako organizační systému. Poskytují způsob, jak klasifikovat a prezentovat programovací elementy, které jsou umístěny do jiných aplikací a aplikací. Všimněte si, že je obor názvů *typ* v tom smyslu, že třídu nebo strukturu – nelze deklarovat jako programovací element mít datový typ oboru názvů.  
  
 Všechny programovací elementy deklarovaný po `Namespace` příkaz patří do daného oboru názvů. Visual Basic nadále kompilována elementy poslední deklarované obor názvů, dokud buď zjistí `End Namespace` příkaz nebo jiné `Namespace` příkaz.  
  
 Pokud obor názvů je již definován i mimo projekt, do něj může přidat elementům programování. K tomuto účelu můžete použít `Namespace` příkaz směrovat jazyka Visual Basic ke kompilaci elementy do daného oboru názvů.  
  
 Můžete použít `Namespace` příkaz jenom na úrovni souboru nebo oboru názvů. To znamená *deklarace kontextu* pro obor názvů musí být zdrojový soubor nebo jiném oboru názvů a nemůže být třída, struktura, modulu, rozhraní nebo postupu. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Je možné deklarovat jeden obor názvů v rámci jiného. Neexistuje žádné striktní omezení úrovní vnoření deklarovat, ale mějte na paměti, že když jiný kód získá přístup k elementy deklarované v nejvnitřnější oboru názvů, musí používat kvalifikace řetězec, který obsahuje všechny názvy oborů názvů v hierarchii vnoření.  
  
## <a name="access-level"></a>Úroveň přístupu  
 Obory názvů jsou zpracovány jako v případě, že mají `Public` úroveň přístupu. Obor názvů je přístupný z kódu kamkoli ve stejném projektu, od jiné projekty, které odkazují na projektu a z libovolného sestavení vytvořené z projektu.  
  
 Programovací elementy deklarovat na úrovni oboru názvů, což znamená v oboru názvů, ale ne do žádného jiného elementu, může mít `Public` nebo `Friend` přístup. Pokud tento parametr nezadáte, úroveň přístupu tohoto například element používá `Friend` ve výchozím nastavení. Prvky, které lze deklarovat na úrovni oboru názvů zahrnují třídy, struktury, moduly, rozhraní, výčty a delegáti. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Namespace kořenové  
 Všechny názvy oborů názvů ve vašem projektu jsou založené na *kořenový obor názvů*. Visual Studio přiřadí název projektu jako výchozí kořenový obor názvů pro všechny kódu v projektu. Například pokud je název projektu `Payroll`, jeho programovací elementy patří do oboru názvů `Payroll`. Pokud je deklarovat `Namespace funding`, úplný název tohoto oboru názvů je `Payroll.funding`.  
  
 Pokud chcete určit existujícího oboru názvů v `Namespace` příkazu, jako v příkladu třída obecné seznamu, můžete nastavit kořenový obor názvů na hodnotu null. Chcete-li to provést, klikněte na tlačítko **vlastnosti projektu** z **projektu** nabídky a zrušte zaškrtnutí **kořenový obor názvů** položky tak, aby pole je prázdné. Pokud není to uděláte v příkladu třída obecný seznam, Visual Basic – kompilátor by trvat `System.Collections.Generic` jako nový obor názvů v rámci projektu `Payroll`, s úplným názvem `Payroll.System.Collections.Generic`.  
  
 Alternativně můžete použít `Global` – klíčové slovo k odkazování na elementy oborů názvů definovaných mimo projekt. Tímto způsobem můžete uchovávat název vašeho projektu jako kořenového oboru názvů. Tím se snižuje riziko neúmyslně slučování vaší elementům programování společně s ty z existujících oborů názvů. Další informace najdete v části "Globální – klíčové slovo ve plně kvalifikované názvy" v [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `Global` – Klíčové slovo lze také použít v příkazu Namespace. To umožňuje definovat oboru názvů z kořenového oboru názvů vašeho projektu. Další informace najdete v části "Globální – klíčové slovo v Namespace příkazy" v [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Řešení potíží.** Kořenového oboru názvů může vést k neočekávaným zřetězování názvy oborů názvů. Pokud provedete odkaz na obory názvů definované mimo projekt, můžete je jako vnořené obory názvů v kořenového oboru názvů construe kompilátoru jazyka Visual Basic. V takovém případě kompilátor nemůže rozpoznat všechny typy, které byla již definována v externí obory názvů. Abyste tomu předešli, buď nastavit na hodnotu null, jak je popsáno v "Kořenový Namespace" kořenový obor názvů nebo použijte `Global` – klíčové slovo na elementy přístup externích oborů názvů.  
  
## <a name="attributes-and-modifiers"></a>Atributy a modifikátory  
 Atributy nelze použít do oboru názvů. Atribut přispívá informace metadat sestavení, která není smysl pro třídění zdroj, například obory názvů.  
  
 Všechny přístupy nebo postup modifikátory nebo jiných modifikátory nemůže použít na obor názvů. Protože není typu, nejsou tyto modifikátory smysluplný.  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí dva obory názvů, jeden v druhém vnořený.  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje více vnořené obory názvů na jeden řádek, a je ekvivalentní k předchozí příklad.  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá třídy definované v předchozích příkladech.  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje kostře novou třídu obecný seznam a přidává ji k <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
