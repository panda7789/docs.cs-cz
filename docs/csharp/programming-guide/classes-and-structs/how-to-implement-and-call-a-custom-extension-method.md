---
title: Postup implementace a volání vlastní metody rozšíření – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: f9937c4b7c6e66af0ee3bc6f6d9ef3b3b1edd530
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241822"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Postup implementace a volání vlastní metody rozšíření (Průvodce programováním v C#)
Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro libovolný typ rozhraní .NET. Kód klienta může použít vaše metody rozšíření přidáním odkazu na knihovnu DLL, který obsahuje, a přidáním direktivy [using](../../language-reference/keywords/using-directive.md) , která určuje obor názvů, ve kterém jsou definovány metody rozšíření.  
  
## <a name="to-define-and-call-the-extension-method"></a>Definování a volání metody rozšíření  
  
1. Definujte statickou [třídu](./static-classes-and-static-class-members.md) , která bude obsahovat metodu rozšíření.  
  
     Třída musí být viditelná pro klientský kód. Další informace o pravidlech přístupnosti najdete v tématu [modifikátory přístupu](./access-modifiers.md).  
  
2. Implementujte metodu rozšíření jako statickou metodu s alespoň stejnou viditelností jako obsahující třídu.  
  
3. První parametr metody určuje typ, na kterém metoda funguje; před ním musí být uveden [Tento](../../language-reference/keywords/this.md) modifikátor.  
  
4. V kódu volání přidejte `using` direktivu pro určení [oboru názvů](../../language-reference/keywords/namespace.md) , který obsahuje třídu metody rozšíření.  
  
5. Zavolejte metody, jako by šlo o metody instance pro daný typ.  
  
     Všimněte si, že první parametr není specifikován voláním kódu, protože představuje typ, na kterém je operátor použit, a kompilátor již zná typ objektu. Stačí zadat argumenty pro parametry 2 až `n` .  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje metodu rozšíření s názvem `WordCount` ve `CustomExtensions.StringExtension` třídě. Metoda pracuje na <xref:System.String> třídě, která je zadána jako první parametr metody. `CustomExtensions`Obor názvů je importován do oboru názvů aplikace a metoda je volána uvnitř `Main` metody.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a>Zabezpečení .NET  
 Metody rozšíření nepředstavují žádné konkrétní chyby zabezpečení. Nemohou být nikdy použity k zosobnění existujících metod pro typ, protože všechny kolize názvů jsou vyřešeny ve prospěch instance nebo statické metody definované samotným typem. Metody rozšíření nemají přístup k žádným soukromým datům v rozšířené třídě.  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Metody rozšíření](./extension-methods.md)
- [LINQ (jazykově integrovaný dotaz)](../../linq/linq-in-csharp.md)
- [Statické třídy a jejich členové](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [internal](../../language-reference/keywords/internal.md)
- [public](../../language-reference/keywords/public.md)
- [this](../../language-reference/keywords/this.md)
- [hosting](../../language-reference/keywords/namespace.md)
