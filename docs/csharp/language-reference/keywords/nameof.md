---
title: nameof (referenční dokumentace jazyka C#)
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 2695095aa4bf2035d8766f3cbcb82f4fbb290e22
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208347"
---
# <a name="nameof-c-reference"></a>nameof (referenční dokumentace jazyka C#)

Použít k získání jednoduchým řetězcem (neúplné) název proměnné, typ nebo člen.  

Při zasílání zpráv o chybách v kódu zapojování odkazy model-view-controller (MVC), která iniciovala změněné vlastnosti události, atd., často chcete zaznamenat název řetězce objektu metodu.  Pomocí `nameof` pomáhá udržovat kódu platný při přejmenování definice.  Před jste museli používat řetězcové literály odkazovat na definice, což je křehká při přejmenování elementy kódu, protože nástroje neznáte Zkontrolujte tyto textové literály.  
  
 A `nameof` výraz má tento formát:  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a>Případy použití klíče  
 Tyto příklady ukazují případů použití klíče pro `nameof`.  
  
 Ověření parametrů:  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 Akce MVC odkazy:  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 Rozhraní INotifyPropertyChanged.:  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 Vlastnost závislosti XAML:  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 Protokolování:  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 Atributy:  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a>Příklady  
 Příklady C#:  
  
```csharp  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
class Test {  
    static void Main (string[] args) {  
        Console.WriteLine(nameof(C)); // -> "C"  
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"  
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"  
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]  
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"  
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]  
        Console.WriteLine(nameof(f)); // -> "f"  
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]  
        // Console.WriteLine(nameof(f<>)); -> [syntax error]  
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]  
    }
}
```  
  
## <a name="remarks"></a>Poznámky  
 Argument `nameof` musí být jednoduchý název, kvalifikovaný název, přístup ke členu, přístupu na základě s zadaného člena nebo tento přístup pomocí zadaného člena.  Výraz argumentu identifikuje definici kód, ale nikdy vyhodnotí.  
  
 Protože argument musí být výraz syntakticky, existují celou řadu věcí, které jsou povoleny a které nejsou užitečné k zobrazení seznamu.  Toto jsou důležité zmínit, které způsobují chyby: předdefinované typy (například `int` nebo `void`), typy s možnou hodnotou Null (`Point?`), pole typů (`Customer[,]`), typy ukazatelů (`Buffer*`) kvalifikovaný alias (`A::B` ) a nevázaných obecných typů (`Dictionary<,>`), předzpracování symboly (`DEBUG`) a popisky (`loop:`).  
  
 Pokud potřebujete získat plně kvalifikovaný název, můžete použít `typeof` výraz spolu s `nameof`.  Příklad:
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 Bohužel `typeof` není konstantní výraz jako `nameof`, takže `typeof` nelze použít ve spojení s `nameof` ve stejné umístí jako `nameof`.  Například následující způsobí chybu kompilace CS0182:
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 V příkladech uvidíte, že můžete použít název typu a přístup k metoda název instance.  Není nutné mít instanci typu, jako v požadovaných vyhodnotí výrazy.  Protože se právě odkazující na název a nepoužíváte instance data, není nutné contrive proměnné instance nebo výraz může být velmi praktické, v některých situacích a použití název typu.  
  
 Členy třídy ve výrazech atribut na třídu, můžete odkazovat.  
  
 Neexistuje žádný způsob, jak získat podpisy informace, jako "`Method1 (str, str)`".  Je možné provést pomocí výrazu, `Expression e = () => A.B.Method1("s1", "s2")`a MemberInfo – ze stromu výsledný výraz pro vyžádání obsahu.  
  
## <a name="language-specifications"></a>Specifikace jazyka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 
