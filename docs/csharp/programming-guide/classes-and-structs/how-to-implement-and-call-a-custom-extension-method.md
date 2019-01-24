---
title: 'Postupy: Implementace a volání vlastní metody rozšíření - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 1bac65ec5aef2846b2b310a65ffbefd5433e93bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652214"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Postupy: Implementace a volání vlastní metody rozšíření (C# Průvodce programováním v)
Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro jakýkoli typ .NET. Klientský kód můžete použít rozšiřující metody přidejte odkaz na knihovnu DLL, která je obsahuje, a přidáním [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktiva, která určuje obor názvů, ve kterém jsou definovány metody rozšíření.  
  
## <a name="to-define-and-call-the-extension-method"></a>K definování a volání metody rozšíření  
  
1.  Definovat statický [třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) obsahuje metody rozšíření.  
  
     Třída musí být viditelná pro klientský kód. Další informace o usnadnění pravidel, naleznete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  Implementovat metodu rozšíření jako statickou metodu s alespoň stejnou viditelnost jako nadřazený třídy.  
  
3.  První parametr metody Určuje typ, který pracuje metodu; musíte začínající [to](../../../csharp/language-reference/keywords/this.md) modifikátor.  
  
4.  Ve volajícím kódu, přidejte `using` – direktiva k určení [obor názvů](../../../csharp/language-reference/keywords/namespace.md) , který obsahuje třídu – metoda rozšíření.  
  
5.  Volání metody, jako kdyby byly metodami instance typu.  
  
     Všimněte si, že první parametr není zadán voláním kódu, protože představuje typ, na které se právě používá operátor a kompilátor zná typu objektu. Budete muset zadat argumenty pro parametry 2 prostřednictvím `n`.  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje metodu rozšíření s názvem `WordCount` v `CustomExtensions.StringExtension` třídy. Metoda pracuje <xref:System.String> třídu, která je zadána jako první parametr metody. `CustomExtensions` Obor názvů se importují do oboru názvů aplikací a metoda je volána v rámci `Main` metody.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód spustit, zkopírujte a vložte ho do jazyka Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio. Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a `using` směrnice pro System.Linq. Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Rozšiřující metody k dispozici žádná konkrétní zabezpečení ohrožení zabezpečení. Se nikdy slouží k zosobnění existující metody na typu, protože jsou vyřešeny všechny kolize názvů ve prospěch instance nebo statické metody definované v samotném typu. Rozšiřující metody nelze přístup k žádným privátním datům ve třídě rozšířené.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [LINQ (Language-Integrated Query)](../../../csharp/linq/linq-in-csharp.md)
- [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
- [internal](../../../csharp/language-reference/keywords/internal.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [this](../../../csharp/language-reference/keywords/this.md)
- [namespace](../../../csharp/language-reference/keywords/namespace.md)
