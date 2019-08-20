---
title: Soukromé konstruktory – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: faa5132845a2d463d3b7d74dc0e0cce21dca61aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596212"
---
# <a name="private-constructors-c-programming-guide"></a>Soukromé konstruktory (Průvodce programováním v C#)
Privátní konstruktor je speciální konstruktor instance. Obvykle se používá ve třídách, které obsahují pouze statické členy. Pokud třída má jeden nebo více privátních konstruktorů a žádné veřejné konstruktory, jiné třídy (s výjimkou vnořených tříd) nemohou vytvářet instance této třídy. Příklad:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Deklarace prázdného konstruktoru brání automatické generaci konstruktoru bez parametrů. Všimněte si, že pokud nepoužíváte modifikátor přístupu s konstruktorem, bude ve výchozím nastavení nadále privátní. Nicméně [soukromý](../../language-reference/keywords/private.md) modifikátor se obvykle používá explicitně k tomu, aby bylo jasné, že třídu nelze vytvořit.  
  
 Soukromé konstruktory se používají k zabránění vytváření instancí třídy, pokud nejsou k dispozici žádná pole nebo metody instance, jako je <xref:System.Math> třída nebo když je volána metoda pro získání instance třídy. Pokud jsou všechny metody ve třídě statické, zvažte vytvoření celé třídy static. Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad třídy používá privátní konstruktor.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Všimněte si, že pokud zrušíte komentář k následujícímu příkazu z příkladu, vygeneruje se chyba, protože konstruktor je nepřístupný z důvodu úrovně ochrany:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete v tématu [Soukromé konstruktory](~/_csharplang/spec/classes.md#private-constructors) ve [ C# specifikaci jazyka](../../language-reference/language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
