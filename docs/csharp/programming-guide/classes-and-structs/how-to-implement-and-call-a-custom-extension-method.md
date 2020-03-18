---
title: Jak implementovat a volat vlastní metodu rozšíření - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7e2092a37c1f042a087e03f4a272139b585156c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705597"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Jak implementovat a volat vlastní metodu rozšíření (C# Programovací průvodce)
Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro libovolný typ .NET. Klientský kód můžete použít metody rozšíření přidáním odkazu na DLL, která je obsahuje a [přidáníusing](../../language-reference/keywords/using-directive.md) směrnice, která určuje obor názvů, ve kterém jsou definovány metody rozšíření.  
  
## <a name="to-define-and-call-the-extension-method"></a>Definování a volání metody rozšíření  
  
1. Definujte statickou [třídu,](./static-classes-and-static-class-members.md) která bude obsahovat metodu rozšíření.  
  
     Třída musí být viditelná pro kód klienta. Další informace o pravidlech usnadnění naleznete [v tématu Access Modifiers](./access-modifiers.md).  
  
2. Implementujte metodu rozšíření jako statickou metodu s alespoň stejnou viditelností jako obsahující třída.  
  
3. První parametr metody určuje typ, na kterém metoda pracuje; musí předcházet [tento](../../language-reference/keywords/this.md) modifikátor.  
  
4. V volajícím kódu `using` přidejte direktivu, která určí [obor názvů,](../../language-reference/keywords/namespace.md) který obsahuje třídu metody rozšíření.  
  
5. Volání metod, jako kdyby byly instance metody na typu.  
  
     Všimněte si, že první parametr není určen voláním kódu, protože představuje typ, na kterém je operátor aplikován, a kompilátor již zná typ objektu. Je třeba zadat pouze argumenty pro `n`parametry 2 až .  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje metodu rozšíření pojmenovanou `WordCount` ve `CustomExtensions.StringExtension` třídě. Metoda pracuje na <xref:System.String> třídu, která je určena jako první parametr metody. Obor `CustomExtensions` názvů je importován do oboru názvů aplikace a `Main` metoda je volána uvnitř metody.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Metody rozšíření nepředstavují žádné konkrétní chyby zabezpečení. Nikdy nelze použít k zosobnění existující metody na typu, protože všechny kolize názvů jsou vyřešeny ve prospěch instance nebo statické metody definované samotným typem. Rozšiřující metody nelze získat přístup k žádné soukromé data v rozšířené třídy.  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Metody rozšíření](./extension-methods.md)
- [LINQ (dotaz integrovaný jazykem)](../../linq/linq-in-csharp.md)
- [Statické třídy a jejich členové](./static-classes-and-static-class-members.md)
- [protected](../../language-reference/keywords/protected.md)
- [Vnitřní](../../language-reference/keywords/internal.md)
- [Veřejné](../../language-reference/keywords/public.md)
- [tohoto provozu](../../language-reference/keywords/this.md)
- [Namespace](../../language-reference/keywords/namespace.md)
