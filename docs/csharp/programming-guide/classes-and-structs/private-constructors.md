---
title: Soukromé konstruktory – Průvodce programováním v C#
description: Privátní konstruktor je speciální konstruktor instance v jazyce C#, který slouží k omezení toho, jak lze objekt vytvořit. Můžou se používat s výrobními metodami nebo jinými idiomy konstrukcemi.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: a6b86ccb870da0262bcbc516e176e00d17724f9f
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864056"
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

Další informace naleznete v tématu [Soukromé konstruktory](~/_csharplang/spec/classes.md#private-constructors) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Konstruktory](./constructors.md)
- [Finalizační metody](./destructors.md)
- [hlášen](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
