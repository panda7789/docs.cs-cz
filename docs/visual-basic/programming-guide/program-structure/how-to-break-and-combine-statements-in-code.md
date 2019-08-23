---
title: 'Postupy: Přerušení a kombinování příkazů v kódu (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 745974523bd747dd23f3cfaf7cb70bb6cd4513f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946201"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Postupy: Přerušení a kombinování příkazů v kódu (Visual Basic)
Při psaní kódu můžete občas vytvořit zdlouhavé příkazy, které vyžadují horizontální posouvání v editoru kódu. I když to nemá vliv na způsob, jakým se váš kód spouští, ztěžuje vám nebo někomu jinému čtení kódu, jak se zobrazuje na monitoru. V takových případech byste měli zvážit rozdělení jednoho dlouhého příkazu na několik řádků.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Přerušení jednoho příkazu na více řádků  
  
- Použijte znak pro pokračování řádku, což je podtržítko (`_`), v místě, kde má být řádek přerušen. Podtržítko musí bezprostředně předcházet mezerou a ihned po něm následovat ukončovací znak (návrat do řádku).  
  
    > [!NOTE]
    > V některých případech, Pokud vynecháte znak pro pokračování řádku, kompilátor Visual Basic implicitně pokračuje v příkazu na dalším řádku kódu. Seznam elementů syntaxe, pro které můžete vynechat znak pro pokračování řádku, naleznete v tématu "implicitní pokračování řádku" v [prohlášeních](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     V následujícím příkladu je příkaz rozdělen na čtyři řádky se znaky pro pokračování řádku, které končí všechny kromě posledního řádku.  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     Použití této sekvence usnadňuje čtení kódu, jak online, tak i po vytištění.  
  
     Znak pro pokračování řádku musí být poslední znak na řádku. Na stejném řádku nemůžete postupovat s jakýmkoli jiným.  
  
     Některá omezení existují, jako na to, kde můžete použít znak pro pokračování řádku; Nemůžete ho například použít uprostřed názvu argumentu. Seznam argumentů lze přerušit pomocí znaku pro pokračování řádku, ale jednotlivé názvy argumentů musí zůstat beze změny.  
  
     Komentář nelze pokračovat pomocí znaku pro pokračování řádku. Kompilátor neověřuje znaky v komentáři pro zvláštní význam. V případě víceřádkového komentáře opakujte symbol komentáře (`'`) na každém řádku.  
  
 I když je umístění každého příkazu na samostatném řádku doporučený způsob, Visual Basic také umožňuje umístit více příkazů na stejný řádek.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Postup umístění více příkazů na stejný řádek  
  
- Příkazy oddělte dvojtečkou (`:`), jako v následujícím příkladu.  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Viz také:

- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
