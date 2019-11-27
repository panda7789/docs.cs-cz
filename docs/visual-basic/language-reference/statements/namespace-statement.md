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
ms.openlocfilehash: 19207a42890640bd82ec547e53eb6d833668e4b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74329648"
---
# <a name="namespace-statement"></a>Namespace – příkaz
Deklaruje název oboru názvů a způsobí, že zdrojový kód, který následuje deklarace, bude zkompilován v rámci tohoto oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a>Součásti  
 Globální  
 Volitelná. Umožňuje definovat obor názvů mimo kořenový obor názvů vašeho projektu. Viz [obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 `name`  
 Požadováno. Jedinečný název, který identifikuje obor názvů. Musí být platný identifikátor Visual Basic. Další informace naleznete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `componenttypes`  
 Volitelná. Prvky, které tvoří obor názvů. Patří mezi ně, ale nejsou omezeny na, výčty, struktury, rozhraní, třídy, moduly, delegáti a jiné obory názvů.  
  
 `End Namespace`  
 Ukončí blok `Namespace`.  
  
## <a name="remarks"></a>Poznámky  
 Obory názvů se používají jako systém organizace. Poskytují způsob klasifikace a přítomnosti programovacích prvků, které jsou vystaveny jiným programům a aplikacím. Všimněte si, že obor názvů není *typu* v tom smyslu, že třída nebo struktura je – nelze deklarovat programový prvek tak, aby měl datový typ oboru názvů.  
  
 Všechny programovací prvky deklarované po `Namespace` příkazu patří do daného oboru názvů. Visual Basic nadále zkompiluje prvky do posledního deklarovaného oboru názvů, dokud nenalezne buď příkaz `End Namespace` nebo jiný příkaz `Namespace`.  
  
 Pokud je již obor názvů definován, dokonce i mimo projekt, můžete do něj přidat programové prvky. K tomu je třeba použít příkaz `Namespace` k přímému Visual Basic ke kompilaci prvků do tohoto oboru názvů.  
  
 Příkaz `Namespace` lze použít pouze na úrovni souboru nebo oboru názvů. To znamená, že *kontext deklarace* pro obor názvů musí být zdrojový soubor nebo jiný obor názvů a nemůže být třída, struktura, modul, rozhraní nebo procedura. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Jeden obor názvů můžete deklarovat v rámci jiného. Neexistuje žádné striktní omezení pro úrovně vnoření, které lze deklarovat, ale mějte na paměti, že pokud jiný kód přistupuje k prvkům deklarovaným v nejvnitřnějším oboru názvů, musí použít řetězec kvalifikace, který obsahuje všechny názvy oborů názvů v vnořování hierarchii.  
  
## <a name="access-level"></a>Úroveň přístupu  
 Obory názvů se považují za, jako by měly `Public` úrovně přístupu. K oboru názvů lze přistoupit z kódu kdekoli ve stejném projektu, z jiných projektů, které odkazují na projekt a ze všech sestavení sestavených z projektu.  
  
 Programovací prvky deklarované na úrovni oboru názvů, což znamená v oboru názvů, ale ne uvnitř žádného jiného prvku, mohou mít `Public` nebo `Friend` přístup. Je-li tento parametr zadán, úroveň přístupu takového prvku používá `Friend` ve výchozím nastavení. Prvky, které lze deklarovat na úrovni oboru názvů, zahrnují třídy, struktury, moduly, rozhraní, výčty a delegáty. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
## <a name="root-namespace"></a>Kořenový obor názvů  
 Všechny názvy oborů názvů v projektu jsou založeny na *kořenovém oboru názvů*. Visual Studio přiřadí název vašeho projektu jako výchozí kořenový obor názvů pro veškerý kód v projektu. Například pokud je projekt pojmenován `Payroll`, jeho programovací prvky patří do oboru názvů `Payroll`. Pokud deklarujete `Namespace funding`, úplný název tohoto oboru názvů je `Payroll.funding`.  
  
 Pokud chcete zadat existující obor názvů v příkazu `Namespace`, jako je například v obecném typu třídy seznamu, můžete nastavit kořenový obor názvů na hodnotu null. Uděláte to tak, že v nabídce **projekt** kliknete na **Vlastnosti projektu** a pak zrušíte výběr položky **kořenového oboru názvů** tak, aby bylo pole prázdné. Pokud jste to neprováděli v obecném příkladu třídy seznamu, Visual Basic kompilátor `System.Collections.Generic` jako nový obor názvů v rámci `Payroll`projektu s úplným názvem `Payroll.System.Collections.Generic`.  
  
 Alternativně můžete použít klíčové slovo `Global` pro odkazování na prvky oborů názvů definovaných mimo váš projekt. To vám umožní zachovat název projektu jako kořenový obor názvů. To snižuje riziko neúmyslného sloučení vašich programových prvků společně s těmito obory názvů. Další informace najdete v oddílu "globální klíčové slovo v plně kvalifikovaném názvu" v tématu [obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 Klíčové slovo `Global` lze také použít v příkazu Namespace. To umožňuje definovat obor názvů mimo kořenový obor názvů vašeho projektu. Další informace najdete v části "globální klíčové slovo v prohlášeních oboru názvů" v tématu [obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
 **Při.** Kořenový obor názvů může vést k neočekávaným zřetězením názvů oborů názvů. Pokud provedete odkaz na obory názvů definované mimo projekt, kompilátor Visual Basic je může vykládat jako vnořené obory názvů v kořenovém oboru názvů. V takovém případě kompilátor nerozpozná žádné typy, které již byly definovány v externích oborech názvů. Abyste tomu předešli, buď nastavte svůj kořenový obor názvů na hodnotu null, jak je popsáno v "kořenovém oboru názvů", nebo použijte klíčové slovo `Global` pro přístup k prvkům externích oborů názvů.  
  
## <a name="attributes-and-modifiers"></a>Atributy a modifikátory  
 Nelze použít atributy na obor názvů. Atribut přispívá k metadatům sestavení, která nejsou smysluplná pro zdrojová třídění, jako jsou například obory názvů.  
  
 Na obor názvů nelze použít žádné modifikátory přístupu nebo procedury ani žádné jiné modifikátory. Protože se nejedná o typ, tyto modifikátory nejsou smysluplné.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje dva obory názvů, jeden vnořený do druhé.  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje více vnořených oborů názvů na jednom řádku a je ekvivalentní k předchozímu příkladu.  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a>Příklad  
 Následující příklad přistupuje ke třídě definované v předchozích příkladech.  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje kostru nové třídy obecných seznamů a přidá ji do oboru názvů <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Imports (obor názvů a typ .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Obory názvů v Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)
