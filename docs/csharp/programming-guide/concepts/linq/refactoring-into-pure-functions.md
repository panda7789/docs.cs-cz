---
title: Refaktoring do čistě funkcí (C#)
description: Naučte se Refaktorovat kód pomocí čistě funkcí. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: cc5dd26923e2edaed34c8f1b742b3dfa1e935e68
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300225"
---
# <a name="refactoring-into-pure-functions-c"></a>Refaktoring do čistě funkcí (C#)

Důležitým aspektem čistě funkční transformace je učení, jak refaktorovat kód pomocí čistě funkcí.  
  
> [!NOTE]
> Běžnou klasifikací při funkčním programování je, že refaktoruje programy pomocí funkce Pure. V Visual Basic a C++ se tato možnost zarovnává s použitím funkcí v odpovídajících jazycích. V jazyce C# se však funkce nazývají metody. Pro účely této diskuze je funkce Pure implementována jako metoda v jazyce C#.  
  
 Jak bylo uvedeno dříve v této části, funkce Pure má dvě užitečné charakteristiky:  
  
- Nemá žádné vedlejší účinky. Funkce nemění žádné proměnné ani data žádného typu mimo funkci.  
  
- Je konzistentní. V případě stejné sady vstupních dat bude vždy vracet stejnou výstupní hodnotu.  
  
 Jedním ze způsobů, jak přecházet do funkčního programování, je refaktorující existující kód, který eliminuje nepotřebné vedlejší účinky a externí závislosti. Tímto způsobem můžete vytvářet čistě verze funkcí stávajícího kódu.  
  
 Toto téma popisuje, co je funkce Pure a co není. [Kurz: manipulace s obsahem v kurzu WordprocessingML dokumentu (C#)](./shape-of-wordprocessingml-documents.md) ukazuje, jak manipulovat s dokumentem WordprocessingML a obsahuje dva příklady refaktorování pomocí funkce Pure.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Vyloučení vedlejších efektů a externích závislostí  
 Následující příklady kontrastují dvě nečisté funkce a funkci Pure.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Nečistá funkce, která mění člena třídy  
 V následujícím kódu není `HyphenatedConcat` funkce čistě funkcí, protože upravuje `aMember` datový člen ve třídě:  
  
```csharp  
public class Program  
{  
    private static string aMember = "StringOne";  
  
    public static void HyphenatedConcat(string appendStr)  
    {  
        aMember += '-' + appendStr;  
    }  
  
    public static void Main()  
    {  
        HyphenatedConcat("StringTwo");  
        Console.WriteLine(aMember);  
    }  
}  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
StringOne-StringTwo  
```  
  
 Všimněte si, že je nedůležité, jestli data, která jsou měněna `public` `private` , mají přístup nebo jsou členem `static` nebo členem instance. Funkce Pure nemění žádná data mimo funkci.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Nečistá funkce, která mění argument  
 Kromě toho následující verze této funkce není čistá, protože upravuje obsah svého parametru, `sb` .  
  
```csharp  
public class Program  
{  
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)  
    {  
        sb.Append('-' + appendStr);  
    }  
  
    public static void Main()  
    {  
        StringBuilder sb1 = new StringBuilder("StringOne");  
        HyphenatedConcat(sb1, "StringTwo");  
        Console.WriteLine(sb1);  
    }  
}  
```  
  
 Tato verze programu vytvoří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila hodnotu (stav) jeho prvního parametru vyvoláním <xref:System.Text.StringBuilder.Append%2A> členské funkce. Všimněte si, že tato změna probíhá navzdory tomu, že `HyphenatedConcat` používá předávání parametru volání podle hodnoty.  
  
> [!IMPORTANT]
> Pro typy odkazů, Pokud předáte parametr podle hodnoty, výsledkem bude kopie odkazu na předaný objekt. Tato kopie je stále přidružená ke stejným datům instance jako původní odkaz (dokud referenční proměnná není přiřazena k novému objektu). Volání po odkazech nemusí nutně vyžadovat, aby funkce mohla upravovat parametr.  
  
### <a name="pure-function"></a>Funkce Pure  
Tato další verze programu ukazuje, jak implementovat `HyphenatedConcat` funkci jako čistě funkci.  
  
```csharp  
class Program  
{  
    public static string HyphenatedConcat(string s, string appendStr)  
    {  
        return (s + '-' + appendStr);  
    }  
  
    public static void Main(string[] args)  
    {  
        string s1 = "StringOne";  
        string s2 = HyphenatedConcat(s1, "StringTwo");  
        Console.WriteLine(s2);  
    }  
}  
```  
  
 Tato verze znovu vytvoří stejný řádek výstupu: `StringOne-StringTwo` . Všimněte si, že pokud chcete zachovat zřetězenou hodnotu, je uložena v mezilehlé proměnné `s2` .  
  
 Jedním z přístupů, které mohou být velmi užitečné, je psaní funkcí, které jsou místně nečisté (to znamená, že deklarují a mění místní proměnné), ale jsou globálně čistě. Tyto funkce mají mnoho z hlediska žádoucích vlastností, ale nemusíte používat rekurzi idiomy, jako je třeba použití rekurze, když by jednoduchá smyčka mohla dosáhnout stejné věci.  
  
## <a name="standard-query-operators"></a>Standardní operátory dotazu  
 Důležitou vlastností standardních operátorů dotazu je to, že jsou implementované jako čisté funkce.  
  
 Další informace najdete v tématu [Přehled standardních operátorů dotazu (C#)](./standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. imperativní programování (C#)](./functional-programming-vs-imperative-programming.md)
