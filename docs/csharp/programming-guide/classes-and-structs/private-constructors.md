---
title: "Soukromé konstruktory (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 79660cd4545fff43ac3dd6ab797fd20c0f882e05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="private-constructors-c-programming-guide"></a>Soukromé konstruktory (Průvodce programováním v C#)
Soukromý konstruktor je konstruktor speciální instanci. Používá se obvykle v tříd, které obsahují pouze statické členy. Pokud třída má jeden nebo více soukromé konstruktory a žádné veřejné konstruktory, ostatní třídy (s výjimkou vnořené třídy) nelze vytvořit instance této třídy. Příklad:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 Prohlášení o prázdný konstruktor brání automatické generování výchozí konstruktor. Všimněte si, že pokud nepoužijete – modifikátor přístupu s konstruktorem ho budete mít privátní ve výchozím nastavení. Ale [privátní](../../../csharp/language-reference/keywords/private.md) modifikátor se obvykle používá k zajištění ji explicitně vymazat, že nelze vytvořit instanci třídy.  
  
 Soukromé konstruktory se používají k zabránění vytvoření instance třídy, pokud nejsou žádné pole instance nebo metody, jako například <xref:System.Math> třídy, nebo když je volána metoda získat instance třídy. Pokud všechny metody ve třídě, jsou statické, zvažte, že dokončení třídu statické. Další informace najdete v části [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Příklad  
 Následuje příklad třídy pomocí soukromý konstruktor.  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 Všimněte si, že pokud zrušte komentář u následujícího příkazu z příkladu, vygeneruje chybu protože konstruktoru je nepřístupný z důvodu jeho úroveň ochrany:  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [privátní](../../../csharp/language-reference/keywords/private.md)  
 [veřejné](../../../csharp/language-reference/keywords/public.md)
