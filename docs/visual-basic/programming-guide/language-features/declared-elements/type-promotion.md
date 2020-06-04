---
title: Propagace typu
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
ms.openlocfilehash: 1e284b99a36cdf0f62aee2c45fd9f3bf544d1d81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410705"
---
# <a name="type-promotion-visual-basic"></a>Propagace typu (Visual Basic)
Při deklaraci programovacího prvku v modulu Visual Basic propaguje svůj rozsah na obor názvů obsahující modul. Tento postup se označuje jako *propagace typů*.  
  
 Následující příklad ukazuje kostru definice modulu a dvou členů tohoto modulu.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 V rámci `projModule` jsou programovací prvky deklarované na úrovni modulu povýšeny na `projNamespace` . V předchozím příkladu `basicEnum` a `innerClass` je povýšen, ale není `numberSub` , protože není deklarována na úrovni modulu.  
  
## <a name="effect-of-type-promotion"></a>Účinek typu propagace  
 Účinek typu propagace je, že řetězec kvalifikace nemusí obsahovat název modulu. Následující příklad vytvoří dvě volání procedury v předchozím příkladu.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 V předchozím příkladu používá první volání kompletní řetězce kvalifikace. To však není nutné z důvodu propagace typu. Druhé volání přistupuje také ke členům modulu bez zahrnutí `projModule` do kvalifikačních řetězců.  
  
## <a name="defeat-of-type-promotion"></a>Připraveno k povýšení typu  
 Pokud obor názvů již obsahuje člena se stejným názvem jako s členem modulu, je pro tohoto člena modulu připraveno typ propagace. Následující příklad znázorňuje kostru definice výčtu a modulu v rámci stejného oboru názvů.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 V předchozím příkladu Visual Basic nemůže propagovat třídu `abc` na, `thisNameSpace` protože již existuje výčet se stejným názvem na úrovni oboru názvů. Chcete-li získat přístup `abcSub` , je nutné použít plný kvalifikační řetězec `thisNamespace.thisModule.abc.abcSub` . Třída je však `xyz` stále povýšen a k nim můžete přistupovat `xyzSub` pomocí kratšího řetězce kvalifikace `thisNamespace.xyz.xyzSub` .  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Připravená propagace typu pro částečné typy  
 Pokud třída nebo struktura uvnitř modulu používá klíčové slovo [Partial](../../../language-reference/modifiers/partial.md) , typ propagace je automaticky připraven pro tuto třídu nebo strukturu, bez ohledu na to, zda obor názvů obsahuje člena se stejným názvem. Další prvky v modulu jsou stále způsobilé pro povýšení typu.  
  
 **Výsledků.** Připravená propagace typu částečné definice může způsobit neočekávané výsledky a dokonce i chyby kompilátoru. Následující příklad ukazuje kostru částečných definic třídy, z nichž jeden je uvnitř modulu.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 V předchozím příkladu může vývojář očekávat, že kompilátor sloučí dvě částečné definice `sampleClass` . Kompilátor však nepovažuje povýšení na částečnou definici uvnitř `sampleModule` . V důsledku toho se pokusí zkompilovat dvě samostatné a jedinečné třídy, jak s názvem, tak `sampleClass` s různými cestami kvalifikace.  
  
 Kompilátor sloučí částečné definice pouze v případě, že jsou jejich plně kvalifikované cesty identické.  
  
## <a name="recommendations"></a>Doporučení  
 Následující doporučení reprezentují dobrý postup programování.  
  
- **Jedinečné názvy.** Pokud máte plnou kontrolu nad pojmenování programovacích prvků, je vždy vhodné použít jedinečné názvy všude. Identické názvy vyžadují dodatečnou kvalifikaci a je možné, že váš kód bude obtížnější číst. Můžou také vést k drobným chybám a neočekávaným výsledkům.  
  
- **Úplná kvalifikace.** Při práci s moduly a dalšími prvky ve stejném oboru názvů je nejbezpečnější přístup vždy používat úplnou kvalifikaci pro všechny programovací prvky. Pokud je u člena modulu připraveno propagace typu a nejste plně kvalifikováni tohoto člena, mohli byste neúmyslně přistupovat k jinému programovacímu prvku.  
  
## <a name="see-also"></a>Viz také

- [Module – příkaz](../../../language-reference/statements/module-statement.md)
- [Namespace – příkaz](../../../language-reference/statements/namespace-statement.md)
- [Částečné](../../../language-reference/modifiers/partial.md)
- [Rozsah v jazyce Visual Basic](scope.md)
- [Postupy: Řízení rozsahu proměnné](how-to-control-the-scope-of-a-variable.md)
- [Odkazy na deklarované elementy](references-to-declared-elements.md)
