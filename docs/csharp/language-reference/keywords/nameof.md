---
title: nameof (referenční dokumentace jazyka C#)
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 726abfd903f37826a247e6e98c0d11f230447550
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078592"
---
# <a name="nameof-c-reference"></a>nameof (referenční dokumentace jazyka C#)

Používá k získání jednoduchého (nekvalifikovaného) řetězcového názvu proměnné, typ nebo člen.  

Při hlášení chyby v kódu, zapojování model-view-controller (MVC) odkazů, ohlásí změněné vlastnosti, události atd., často chcete zaznamenat název řetězce objektu metodu.  Pomocí `nameof` pomáhá udržovat váš kód platný při přejmenování definice.  Dříve jste museli používat řetězcové literály k odkazování na definice, které je třeba při přejmenování prvků kódu, protože nejste jisti nástroje ke kontrole tyto řetězcové literály.  
  
 A `nameof` výrazu má tento tvar:  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a>Případy použití klíčů  
 Tyto příklady ukazují, případy použití klíče pro `nameof`.  
  
 Ověřte parametry:  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 Odkazy na akce MVC:  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 INotifyPropertyChanged:  
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
 Některé příklady jazyka C#:  
  
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
 Argument `nameof` musí být jednoduchý název, úplný název, přístup ke členu, základní přístup pomocí zadaného člena nebo tento přístup pomocí zadaného člena.  Výraz argumentu identifikuje definice kódu, ale nikdy není vyhodnocen.  
  
 Vzhledem k tomu, že argument musí být výraz syntakticky, existuje mnoho věcí zakázané, které nejsou vhodné seznamu.  Za zmínku, která způsobují chyby jsou následující: předdefinované typy (například `int` nebo `void`), typy připouštějící hodnotu Null (`Point?`), pole typů (`Customer[,]`), typy ukazatelů (`Buffer*`) kvalifikovaný alias (`A::B` ) a nevázaných obecných typů (`Dictionary<,>`), předzpracování symboly (`DEBUG`) a popisky (`loop:`).  
  
 Pokud je potřeba získat plně kvalifikovaný název, můžete použít `typeof` výrazu spolu s `nameof`.  Příklad:
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 Bohužel `typeof` není konstantní výraz, stejně jako `nameof`, takže `typeof` nelze použít ve spojení s `nameof` ve stejné umístění jako `nameof`.  Následující by například způsobila chybu kompilace CS0182:
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 V příkladech se zobrazí, že můžete použít název typu a přístup k názvu metody instance.  Nemusíte mít instanci typu, jako požadavků ve vyhodnoceném výrazy.  Protože se právě odkazující na název a bez použití instance data, není potřeba contrive instanci proměnné nebo výrazu může být příliš pohodlné, v některých situacích a názvu typu.  
  
 Můžete odkazovat na členy třídy ve výrazech atribut ve třídě.  
  
 Neexistuje žádný způsob, jak získat podpisy informace, jako "`Method1 (str, str)`".  Jedním ze způsobů, který je použití výrazu `Expression e = () => A.B.Method1("s1", "s2")`a o přijetí změn MemberInfo z výsledný strom výrazu.  
  
## <a name="language-specifications"></a>Specifikace jazyka  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [typeof](../../../csharp/language-reference/keywords/typeof.md)  
