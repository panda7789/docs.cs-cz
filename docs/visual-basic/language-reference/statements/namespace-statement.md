---
title: Namespace – příkaz (Visual Basic)
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
ms.openlocfilehash: 28016763b2cef2e8b8954f486bbbdb6930b5364c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514984"
---
# <a name="namespace-statement"></a>Namespace – příkaz
Deklaruje název oboru názvů a způsobí, že zdrojový kód, který následuje za deklarací zkompiluje uvnitř tohoto oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Součásti  
 Globální  
 Volitelné. Můžete zadat obor názvů mimo kořenový obor názvů vašeho projektu. Zobrazit [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Požadováno. Jedinečný název, který identifikuje obor názvů. Musí být platným identifikátorem jazyka Visual Basic. Další informace najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Volitelné. Elementy, které tvoří obor názvů. Ty zahrnují, ale nejsou omezené na výčty, struktury, rozhraní, třídy, moduly, delegáty a jiných oborech názvů.  
  
 `End Namespace`  
 Ukončí `Namespace` bloku.  
  
## <a name="remarks"></a>Poznámky  
 Obory názvů slouží jako systém organizace. Poskytují způsob, jak klasifikovat a k dispozici programovací prvky, které jsou vystaveny další programy a aplikace. Všimněte si, že je obor názvů *typ* v tom smyslu, že třídu nebo strukturu – nelze deklarovat programovací element má datový typ oboru názvů.  
  
 Všechny programovací elementy deklarované až po `Namespace` příkaz patří do daného oboru názvů. Visual Basic i nadále kompilaci prvky do posledního deklarovaného oboru názvů, dokud nenarazí na buď `End Namespace` příkazu nebo jiného `Namespace` příkazu.  
  
 Pokud obor názvů je již definován i vně projektu, můžete do něj přidat programovací prvky. K tomuto účelu můžete použít `Namespace` příkaz pro přesměrování jazyka Visual Basic pro kompilaci prvky do daného oboru názvů.  
  
 Můžete použít `Namespace` příkaz pouze na úrovni souboru nebo oboru názvů. To znamená, že *kontext deklarace* pro obor názvů musí být zdrojový soubor nebo jiný obor názvů a nemůže být třída, struktura, modul, rozhraní nebo postupu. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Je možné deklarovat jeden obor názvů v rámci jiného. Neexistuje žádné striktní omezení úrovní vnoření lze deklarovat, ale mějte na paměti, že když jiný kód přistupuje k elementy deklarované v nejvnitřnější obor názvů, musíte použít kvalifikace řetězec obsahující všechny názvy oborů názvů v hierarchii vnoření.  
  
## <a name="access-level"></a>Úroveň přístupu  
 Obory názvů jsou zpracovávány jako by to mají `Public` úroveň přístupu. Obor názvů je přístupný z kódu kdekoli ve stejném projektu, než ostatní projekty, které odkazují na projekt a z libovolné sestavení vytvořeného z projektu.  
  
 Programovací elementy deklarované na úrovni oboru názvů, což znamená v oboru názvů, ale ne uvnitř jiného elementu, může mít `Public` nebo `Friend` přístup. Pokud tento parametr zadán, úroveň přístupu tohoto elementu používá `Friend` ve výchozím nastavení. Prvky, které je možné deklarovat na úrovni oboru názvů zahrnují třídy, struktury, moduly, rozhraní, výčty a delegáti. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Kořenové Namespace  
 Všechny názvy oborů názvů v projektu jsou založeny na *kořenový obor názvů*. Jako výchozí obor názvů root pro veškerý kód v projektu sady Visual Studio přiřadí název vašeho projektu. Například, pokud je název vašeho projektu `Payroll`, jeho programovací prvky patří do oboru názvů `Payroll`. Pokud deklarujete `Namespace funding`, celý název daného oboru názvů `Payroll.funding`.  
  
 Pokud chcete zadat existující obor názvů v `Namespace` příkazu, jako v příkladu třída obecný seznam, můžete nastavit váš kořenový obor názvů na hodnotu null. Chcete-li to provést, klikněte na tlačítko **vlastnosti projektu** z **projektu** nabídky a potom zrušte zaškrtnutí políčka **kořenový obor názvů** položky tak, že je pole prázdné. Pokud není to v příkladu obecný seznam tříd, kompilátor jazyka Visual Basic by trvalo `System.Collections.Generic` jako nový obor názvů v rámci projektu `Payroll`, s úplným názvem `Payroll.System.Collections.Generic`.  
  
 Alternativně můžete použít `Global` – klíčové slovo neodkazuje na prvky oborů názvů definován vně vašeho projektu. To vám umožňuje zachovat název projektu jako kořenový obor názvů. Tím omezíte možnost neúmyslně sloučení vaše programovací prvky spolu s ty stávající obory názvů. Další informace najdete v části "Globální – klíčové slovo v plně kvalifikované názvy" v [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `Global` – Klíčové slovo lze také použít v příkazu Namespace. Tímto způsobem můžete definovat obor názvů mimo kořenový obor názvů vašeho projektu. Další informace najdete v části "Globální – klíčové slovo v Namespace příkazy" v [obory názvů v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Řešení potíží.** Kořenový obor názvů může vést k neočekávaným zřetězení názvy oborů názvů. Pokud odkaz na obory názvů definované vně projektu, může kompilátor jazyka Visual Basic provést construe jako vnořené obory názvů v kořenovém oboru názvů. V takovém případě kompilátor nedokáže rozpoznat všechny typy, které jste již byla definována v externí obory názvů. Abyste tomu předešli, nastavit váš kořenový obor názvů na hodnotu null, jak je popsáno v "Kořenový Namespace", nebo použít `Global` – klíčové slovo prvkům přístup externí oborů názvů.  
  
## <a name="attributes-and-modifiers"></a>Atributy a modifikátory  
 Nelze použít atributy do oboru názvů. Atribut přispívá informace metadat sestavení, která není smysl pro třídění zdroje, jako je například obory názvů.  
  
 Přístup nebo proceduru modifikátory nebo jiných Modifikátory nelze použít pro obor názvů. Protože se nejedná typ, nejsou tyto modifikátory smysluplné.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje dva obory názvů, jeden v druhém vnořený.  
  
 [!code-vb[VbVbalrStatements#43](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje několik vnořené obory názvů na jednom řádku a je ekvivalentní předchozí příklad.  
  
 [!code-vb[VbVbalrStatements#41](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_2.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přistupuje k třídy definované v předchozích příkladech.  
  
 [!code-vb[VbVbalrStatements#42](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/namespace-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje kostra novou třídu obecný seznam a přidá jej do <xref:System.Collections.Generic?displayProperty=nameWithType> oboru názvů.  
  
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
