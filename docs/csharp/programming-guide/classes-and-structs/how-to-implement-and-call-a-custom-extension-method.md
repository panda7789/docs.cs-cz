---
title: "Postupy: Implementace a volání vlastní metody rozšíření (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a277412c69d26f20721381d9cfa839c7f082f2f2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a>Postupy: Implementace a volání vlastní metody rozšíření (Průvodce programováním v C#)
Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro jakýkoli typ rozhraní .NET. Kód klienta můžete použít rozšiřující metody přidat odkaz na knihovnu DLL, která je obsahuje, a přidáním [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktiva, která určuje obor názvů, ve kterém jsou definovány rozšiřující metody.  
  
## <a name="to-define-and-call-the-extension-method"></a>K definování a volání metody rozšíření  
  
1.  Definování statického [třída](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) tak, aby obsahovala metodě rozšíření.  
  
     Třída musí být viditelná pro kódu klienta. Další informace o usnadnění pravidla najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
2.  Implementace metody rozšíření jako statickou metodu s alespoň viditelná stejně jako obsahující třídy.  
  
3.  První parametr metody Určuje typ, který zpracovává metodu; ho musí předcházet [to](../../../csharp/language-reference/keywords/this.md) modifikátor.  
  
4.  Přidejte kód volání `using` – direktiva k určení [obor názvů](../../../csharp/language-reference/keywords/namespace.md) obsahující rozšíření metoda třída.  
  
5.  Volání metody, jako kdyby byly metody instance typu.  
  
     Upozorňujeme, že první parametr není zadán voláním kódu, protože představuje typ, na kterém se používá operátor a kompilátor již zná typ objektu. Budete muset zadat argumenty pro parametry 2 prostřednictvím `n`.  
  
## <a name="example"></a>Příklad  
 Následující příklad implementuje metody rozšíření s názvem `WordCount` v `CustomExtensions.StringExtension` třídy. Metoda zpracovává <xref:System.String> třídy, která je zadána jako první parametr metody. `CustomExtensions` Obor názvů je importovat do oboru názvů aplikací a metoda je volána v rámci `Main` metoda.  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Pokud chcete spustit tento kód, zkopírujte a vložte ho do Visual C# projektu konzolové aplikace vytvořené v [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)]. Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a obsahuje odkaz na System.Core.dll a `using` direktivy pro System.Linq. Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Rozšiřující metody k dispozici žádná konkrétní bezpečnostní ohrožení zabezpečení. Se nikdy slouží k zosobnění existující metody podle typu, protože jsou vyřešeny všechny kolize názvů považuje instance nebo statickou metodu definované vlastní typ. Rozšiřující metody nelze přístup k žádným privátní datům ve třídě rozšířené.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [this](../../../csharp/language-reference/keywords/this.md)  
 [namespace](../../../csharp/language-reference/keywords/namespace.md)
