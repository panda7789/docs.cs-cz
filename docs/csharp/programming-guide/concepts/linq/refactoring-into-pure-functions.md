---
title: Refaktoring do čistých funkcí (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253102"
---
# <a name="refactoring-into-pure-functions-c"></a>Refaktoring do čistých funkcí (C#)

Důležitým aspektem čistě funkční transformace je naučit se refaktorovat kód pomocí čisté funkce.  
  
> [!NOTE]
> Běžnou nomenklaturou ve funkčním programování je, že refaktorujete programy pomocí čistých funkcí. V jazyce Visual Basic a C++ to zarovná s použitím funkcí v příslušných jazycích. Však v C#, funkce se nazývají metody. Pro účely této diskuse je čistá funkce implementována jako metoda v c#.  
  
 Jak je uvedeno dříve v této části, čistá funkce má dvě užitečné vlastnosti:  
  
- Nemá žádné vedlejší účinky. Funkce nemění žádné proměnné nebo data jakéhokoli typu mimo funkci.  
  
- Je to konzistentní. Vzhledem ke stejné sadě vstupních dat vždy vrátí stejnou výstupní hodnotu.  
  
 Jedním ze způsobů přechodu na funkční programování je refaktorovat existující kód k odstranění zbytečných vedlejších účinků a externích závislostí. Tímto způsobem můžete vytvořit čistě funkční verze existujícího kódu.  
  
 Toto téma popisuje, co je čistá funkce a co není. [Kurz: Manipulace s obsahem v dokumentu WordprocessingML (C#)](./shape-of-wordprocessingml-documents.md) kurz ukazuje, jak manipulovat s dokumentem WordprocessingML a obsahuje dva příklady, jak refaktorovat pomocí čisté funkce.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Odstranění vedlejších účinků a externích závislostí  
 Následující příklady kontrastují dvě nečisté funkce a čistou funkci.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Nečistá funkce, která mění člen třídy  
 V následujícím kódu `HyphenatedConcat` funkce není čistě, protože upravuje `aMember` datový člen ve třídě:  
  
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
  
 Všimněte si, že je irelevantní, zda má upravná data `public` nebo `private` přístup, nebo je `static` členem nebo členem instance. Čistá funkce nemění žádná data mimo funkci.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Nečistá funkce, která mění argument  
 Kromě toho následující verze stejné funkce není čistá, protože upravuje obsah svého `sb`parametru .  
  
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
  
 Tato verze programu vytváří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila hodnotu (stav) svého prvního parametru <xref:System.Text.StringBuilder.Append%2A> vyvoláním členské funkce. Všimněte si, že k `HyphenatedConcat` této změně dochází navzdory skutečnosti, že používá předávání parametru call-by-value.  
  
> [!IMPORTANT]
> Pro typy odkazů, pokud předáte parametr podle hodnoty, výsledkem je kopie odkazu na předávaný objekt. Tato kopie je stále přidružena ke stejným datům instance jako původní odkaz (dokud není referenční proměnná přiřazena novému objektu). Volání podle odkazu není nutně nutné pro funkci upravit parametr.  
  
### <a name="pure-function"></a>Čistá funkce  
Tato další verze programu ukazuje, `HyphenatedConcat` jak implementovat funkci jako čistou funkci.  
  
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
  
 Opět platí, že tato verze produkuje `StringOne-StringTwo`stejný řádek výstupu: . Všimněte si, že chcete-li zachovat zřetězenou `s2`hodnotu, je uložen v zprostředkující proměnné .  
  
 Jeden přístup, který může být velmi užitečné, je psát funkce, které jsou místně nečisté (to znamená, že deklarují a upravují místní proměnné), ale jsou globálně čisté. Tyto funkce mají mnoho žádoucí charakteristiky kompozity, ale vyhnout se některé více spletité funkční programovací idiomy, jako je například nutnost používat rekurze, když jednoduchá smyčka by dosáhnout totéž.  
  
## <a name="standard-query-operators"></a>Standardní operátory dotazů  
 Důležitou charakteristikou standardních operátorů dotazů je, že jsou implementovány jako čisté funkce.  
  
 Další informace naleznete [v tématu Přehled operátorů standardních dotazů (C#)](./standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Úvod do čistě funkčních transformací (C#)](./introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. imperativní programování (C#)](./functional-programming-vs-imperative-programming.md)
