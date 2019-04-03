---
title: Propagace typu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: f7ac6bfb944da8bd50e035ba97b2b513176dc661
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838869"
---
# <a name="type-promotion-visual-basic"></a>Propagace typu (Visual Basic)
Při deklaraci programovací element v modulu jazyka Visual Basic podporuje jeho obor názvů obsahující modul. To se označuje jako *zadejte povýšení*.  
  
 Následující příklad ukazuje definici kostru modulu a dva členy tohoto modulu.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 V rámci `projModule`, programovací elementy deklarované na úrovni modulu jsou povýšeny do `projNamespace`. V předchozím příkladu `basicEnum` a `innerClass` jsou povýšeny, ale `numberSub` není, protože nemá nastavenou deklaraci na úrovni modulu.  
  
## <a name="effect-of-type-promotion"></a>Účinek propagace typu  
 Efekt propagace typu je, že řetězec kvalifikace nemusí obsahovat název modulu. Následující příklad provede dvě volání do procedury v předchozím příkladu.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 V předchozím příkladu používá první volání řetězce úplný kvalifikace. Ale to není nezbytné z důvodu propagace typu. Druhý také přístup k modulu členy volat bez zahrnutí `projModule` v řetězcích kvalifikace.  
  
## <a name="defeat-of-type-promotion"></a>Odpojovací propagace typu  
 Pokud obor názvů již obsahuje člena se stejným názvem jako členský modul, propagace typu není zrušena pro tohoto člena modulu. Následující příklad ukazuje definici kostru výčet a modul v rámci stejného oboru názvů.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 V předchozím příkladu, Visual Basic nelze zvýšit úroveň třídy `abc` k `thisNameSpace` protože výčet na úrovni oboru názvů se stejným názvem již existuje. Pro přístup k `abcSub`, je nutné použít úplnou kvalifikace řetězec `thisNamespace.thisModule.abc.abcSub`. Však třídy `xyz` stále povýšen, a také zpřístupnit `xyzSub` s kratší řetězec kvalifikace `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Odpojovací propagace typu pro částečné typy  
 Pokud třída nebo struktura uvnitř modul používá [částečné](../../../../visual-basic/language-reference/modifiers/partial.md) – klíčové slovo, propagace typu není automaticky zrušena třídy nebo struktury, zda je obor názvů obsahuje člena se stejným názvem. Další prvky v modulu jsou i dál nárok pro povýšení typu.  
  
 **Důsledky.** Odpojovací propagace typu Částečná definice může způsobit neočekávané výsledky a dokonce i chyby kompilátoru. Následující příklad ukazuje kostru částečné definice třídy, z nichž jeden je uvnitř modulu.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 V předchozím příkladu, vývojář může očekávat kompilátoru sloučit dva Částečná definice `sampleClass`. Však kompilátor nebere v úvahu propagační akce pro částečnou definici uvnitř `sampleModule`. V důsledku toho se pokusí zkompilovat dvě samostatné a odlišné třídy, oba s názvem `sampleClass` , ale s jinou kvalifikace cesty.  
  
 Kompilátor sloučí částečné definice pouze v případě jejich úplné cesty jsou identické.  
  
## <a name="recommendations"></a>Doporučení  
 Následující doporučení představují dobrý postup programování.  
  
-   **Jedinečné názvy.** Až budete mít plnou kontrolu nad pojmenování programovací prvky, je vždy vhodné použít všude, kde jedinečné názvy. Identické názvy vyžadovat dodatečné kvalifikace a mohou znesnadnit kódu ke čtení. Může se také vést k drobným chybám a neočekávané výsledky.  
  
-   **Úplné kvalifikace.** Při práci s moduly a další prvky v stejný obor názvů nejbezpečnější přístup je vždycky potřeba použít úplnou kvalifikace pro všechny programovací prvky. Propagace typu není zrušena pro člena modulu a nemáte kvalifikovanou plně tohoto člena, může nechtěně přístup různé programovací element.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Module](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Příkaz Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Postupy: Řízení rozsahu proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
