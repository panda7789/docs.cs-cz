---
title: Soukromé konstruktory – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705441"
---
# <a name="private-constructors-c-programming-guide"></a>Soukromé konstruktory (Průvodce programováním v C#)
Soukromý konstruktor je konstruktor zvláštní instance. Obecně se používá ve třídách, které obsahují pouze statické členy. Pokud třída má jeden nebo více soukromých konstruktorů a žádné veřejné konstruktory, jiné třídy (s výjimkou vnořené třídy) nelze vytvořit instance této třídy. Například:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Deklarace prázdnékonstruktor zabraňuje automatické generování konstruktoru bez parametrů. Všimněte si, že pokud nepoužijete modifikátor přístupu s konstruktorem, bude ve výchozím nastavení stále soukromý. [Privátní](../../language-reference/keywords/private.md) modifikátor se však obvykle používá explicitně, aby bylo jasné, že třídu nelze vytvořit instanci.  
  
 Soukromé konstruktory se používají k zabránění vytváření instancí třídy, pokud <xref:System.Math> neexistují žádná pole instance nebo metody, jako je například třída, nebo když je metoda volána k získání instance třídy. Pokud jsou všechny metody ve třídě statické, zvažte vytvoření úplné třídy statické. Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Příklad  
 Následuje příklad třídy pomocí soukromého konstruktoru.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Všimněte si, že pokud odkomentujete následující příkaz z příkladu, vygeneruje chybu, protože konstruktor je nepřístupný z důvodu úrovně ochrany:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  

Další informace naleznete [v tématu Private konstruktory](~/_csharplang/spec/classes.md#private-constructors) v [c# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
- [Soukromé](../../language-reference/keywords/private.md)
- [Veřejné](../../language-reference/keywords/public.md)
