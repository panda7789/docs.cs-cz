---
title: Refaktoring do čistých funkcí (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 3a498588e9ca1ab85602946b75b593804fa0953a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596881"
---
# <a name="refactoring-into-pure-functions-c"></a>Refaktoring do čistých funkcí (C#)

Důležitou součástí čistě funkčním transformacím je učit, jak Refaktorovat kód pomocí čisté funkce.  
  
> [!NOTE]
>  Běžné do funkčního programování se, že Refaktorovat programy pomocí čisté funkce. V jazyce Visual Basic a C++ ten je v souladu s použitím funkce v příslušné jazyky. V jazyce C#, ale funkce jsou volány metody. Pro účely této diskuse je implementovaný čistě funkce jako metody v jazyce C#.  
  
 Jak je uvedeno dříve v této části, čistě funkci má dvě užitečné vlastnosti:  
  
- Nemá žádné vedlejší účinky. Funkce nezmění žádné proměnné nebo dat libovolného typu mimo funkci.  
  
- To je konzistentní. S ohledem stejnou sadu vstupních dat, vždycky vrátí stejnou hodnotu výstup.  
  
 Jeden způsob, jak přechod do funkčního programování je Refaktorujte již existující kód k odstranění nepotřebných vedlejší účinky a externích závislostí. Tímto způsobem můžete vytvořit čistě funkce verze stávajícího kódu.  
  
 Toto téma popisuje čistě funkce je a co není. [Kurzu: Manipulace s obsahem v dokumentu WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) kurz ukazuje, jak pracovat s dokumentu WordprocessingML a obsahuje dva příklady toho, jak refaktorace pomocí čisté funkce.  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a>Odstranění vedlejší účinky a externí závislosti  
 Následující příklady kontrastu dvě funkce čistě a čistě funkce.  
  
### <a name="non-pure-function-that-changes-a-class-member"></a>Čistě funkce, která se mění členem třídy.  
 V následujícím kódu `HyphenatedConcat` funkce není čistě funkcí, protože upravuje `aMember` datový člen třídy:  
  
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
  
 Tento kód vytvoří následující výstup:  
  
```  
StringOne-StringTwo  
```  
  
 Všimněte si, že je bezvýznamná toho, jestli má úpravy dat `public` nebo `private` přístup, nebo je `static` člen nebo člen instance. Čistě funkce nemění žádná data mimo funkci.  
  
### <a name="non-pure-function-that-changes-an-argument"></a>Čistě funkce, která se mění Argument  
 Následující verze stejné funkce kromě toho není čistě, protože mění obsah svůj parametr, `sb`.  
  
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
  
 Tuto verzi programu vytváří stejný výstup jako první verze, protože `HyphenatedConcat` funkce změnila jejím prvním parametrem (stav) hodnota vyvoláním <xref:System.Text.StringBuilder.Append%2A> členskou funkci. Všimněte si, že tato změna nastane bez ohledu na tom, který `HyphenatedConcat` používá předávání parametrů volání podle hodnoty.  
  
> [!IMPORTANT]
>  Pro typy odkazů Pokud předáte parametr podle hodnoty, výsledkem zkopírovat odkaz na objekt je předán. Tato kopie je stále spojena se stejná data jako odkaz na původní instanci (až do nového objektu přiřadí proměnná odkaz). Volání odkazem se nutně nevyžaduje pro funkci, kterou chcete upravit parametr.  
  
### <a name="pure-function"></a>Pure – funkce  
Tato další verze program ukazuje, jak implementovat `HyphenatedConcat` fungovat jako čistě funkce.  
  
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
  
 Znovu, vytvoří tato verze stejného řádku výstupu: `StringOne-StringTwo`. Všimněte si, že pokud chcete zachovat zřetězené hodnotě, uloží se zprostředkující proměnné `s2`.  
  
 Je jedním z přístupů, které mohou být velmi užitečná k zápisu funkcí, které jsou místně znečištěná (to znamená, že deklarace a upravit místní proměnné), ale jsou globálně čistě. Tyto funkce mají mnoho vlastností žádoucí skládání, ale Vyhněte se některé z více složitými funkční programovací idiomy, jako je například museli použít rekurzi při jednoduché smyčky by provést totéž.  
  
## <a name="standard-query-operators"></a>Standardní operátory dotazu  
 Důležitou vlastnost operátory standardního dotazu je, že jsou implementovány jako čistě funkce.  
  
 Další informace najdete v tématu [přehled standardních operátorů dotazu (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Úvod k čistě funkčním transformacím (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Funkční programování vs. Imperativní programování (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
