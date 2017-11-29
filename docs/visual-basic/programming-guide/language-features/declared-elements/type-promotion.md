---
title: Propagace typu (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3a55c023afe7afe96f862f0b3cbbdb03a15b902
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-promotion-visual-basic"></a>Propagace typu (Visual Basic)
Když je deklarovat programovací element v modulu, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zvýší úroveň jeho oboru do oboru názvů, který obsahuje modul. To se označuje jako *zadejte povýšení*.  
  
 Následující příklad ukazuje definici kostru modulu a dva členové tohoto modulu.  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 V rámci `projModule`, programovací elementy deklarovat na úrovni modulu povýšené na `projNamespace`. V předchozím příkladu `basicEnum` a `innerClass` povýšené, ale `numberSub` není, protože nemá na úrovni modulu.  
  
## <a name="effect-of-type-promotion"></a>Účinek propagace typu  
 Účinek povýšení typ je řetězec kvalifikace nemusí obsahovat název modulu. Následující příklad volá dvě podle postupu v předchozím příkladu.  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 V předchozím příkladu použije první volání dokončení kvalifikace řetězce. Je to ale není nutné z důvodu propagace typu. Druhý volání také přístupů modulu členy bez zahrnutí `projModule` v řetězcích kvalifikaci.  
  
## <a name="defeat-of-type-promotion"></a>Odpojovací propagace typu  
 Pokud obor názvů již obsahuje člena se stejným názvem jako člena modulu, typu povýšení se nepotlačí pro tento člen modulu. Následující příklad ukazuje definici kostru výčet a modul v rámci stejného oboru názvů.  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 V předchozím příkladu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nelze zvýšit úroveň třída `abc` k `thisNameSpace` protože výčet na úrovni oboru názvů se stejným názvem již existuje. Pro přístup k `abcSub`, musíte použít úplnou kvalifikace řetězec `thisNamespace.thisModule.abc.abcSub`. Ale třídy `xyz` je stále povýšit, a dostanete `xyzSub` s kratší řetězec kvalifikace `thisNamespace.xyz.xyzSub`.  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Odpojovací propagace typu pro částečné typy  
 Pokud třídu nebo strukturu uvnitř modul používá [částečné](../../../../visual-basic/language-reference/modifiers/partial.md) – klíčové slovo, propagace typu je automaticky nepotlačí pro tuto třídu nebo strukturu, zda obor názvů obsahuje člena se stejným názvem. Další prvky v modulu jsou stále vhodné pro typ akce.  
  
 **Důsledky.** Odpojovací propagace typu částečné definice může způsobit neočekávané výsledky a i chyby kompilátoru. Následující příklad ukazuje kostru částečné definice třídy, z nichž jeden je uvnitř modul.  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 V předchozím příkladu může vývojář očekávat kompilátoru sloučit dva částečné definice `sampleClass`. Ale kompilátor nebere v úvahu povýšení pro definici částečné uvnitř `sampleModule`. V důsledku toho pokusí zkompilovat dvě samostatné a jiné třídy, i s názvem `sampleClass` , ale s jinou kvalifikace cesty.  
  
 Kompilátor sloučí částečné definice jenom v případě, že jsou identické jejich plně kvalifikované cesty.  
  
## <a name="recommendations"></a>Doporučení  
 Následující doporučení představují vhodné programování.  
  
-   **Jedinečné názvy.** Když máte plnou kontrolu nad názvů programovací elementy, vždycky je vhodné použít všude, kde jedinečné názvy. Identické názvy vyžadovat další kvalifikace a mohl provádět kódu těžší ke čtení. Také mohou vést k jemně chyb a neočekávané výsledky.  
  
-   **Úplné kvalifikaci.** Při práci s moduly a další prvky v o stejný obor názvů, nejbezpečnější způsob je vždy nutné použít úplnou kvalifikaci pro všechny programovací elementy. Pokud je propagace typu nepotlačí pro člena modulu a které nemohou být plně tohoto člena, může nechtěně přístup různé programovací element.  
  
## <a name="see-also"></a>Viz také  
 [Module – příkaz](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Namespace – příkaz](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Částečné](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Postupy: řízení rozsahu proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
