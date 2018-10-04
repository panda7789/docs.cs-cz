---
title: Rozšíření ladění pomocí atributů zobrazení ladicího programu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4150658f713e626c5578c21cfada0f6410cbd37b
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779592"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Rozšíření ladění pomocí atributů zobrazení ladicího programu

Povolit vývojář atributů zobrazení ladicího programu typu, který určuje a nejlépe rozumí chování za běhu tohoto typu, také určit, co typu bude vypadat jako, který se zobrazí v ladicí program. Kromě toho ladicí program zobrazit atributy, které poskytují `Target` vlastnost jde použít na úrovni sestavení uživatelé bez vědomí zdrojového kódu. <xref:System.Diagnostics.DebuggerDisplayAttribute> Atribut určuje, jak je zobrazeno typ nebo člen v oknech proměnných ladicího programu. <xref:System.Diagnostics.DebuggerBrowsableAttribute> Atribut určuje, zda a jak pole nebo vlastnost se zobrazí v oknech proměnných ladicího programu. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut určuje náhradní typ. nebo proxy server, pro typ a změní způsob, jak se zobrazí typ v oknech ladicího programu. Při zobrazení proměnná, která má proxy server nebo náhradní typ. proxy zastupuje původní typ, v okně zobrazení ladicího programu. V okně proměnné ladicího programu se zobrazí pouze veřejné členy typu proxy. Soukromé členy nejsou zobrazeny.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Použití debuggerdisplayattribute –  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor obsahuje jediný argument: řetězec, který se zobrazí ve sloupci Hodnota pro instance daného typu. Tento řetězec může obsahovat složených závorek ({a}). Text v rámci dvojici závorek je vyhodnocen jako výraz. Například následující kód jazyka C# způsobí, že se "Count = 4" který se má zobrazit, pokud je vybrána na symbol plus (+) rozbalte zobrazení ladicího programu pro instanci `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Atributy použité na vlastnosti odkazuje ve výrazu nebudou zpracovány. Pro kompilátor jazyka C# je povolen obecné výraz, který má pouze implicitní přístup k tomuto odkazu pro aktuální instanci cílového typu. Výraz je omezená; není k dispozici přístup pro aliasy, místní hodnoty nebo ukazatele. V kódu jazyka C#, můžete použít obecné výraz mezi závorkami, ke kterým implicitní přístup `this` ukazatele pro aktuální instanci pouze cílového typu.

Například, pokud objekt jazyka C# má překryté `ToString()`, ladicí program bude volat přepsání a zobrazit její výsledek místo standardní `{<typeName>}.` proto pokud mají přepsat `ToString()`, není potřeba použít <xref:System.Diagnostics.DebuggerDisplayAttribute>. Pokud používáte obě, <xref:System.Diagnostics.DebuggerDisplayAttribute> atribut má přednost před `ToString()` přepsat.

## <a name="using-the-debuggerbrowsableattribute"></a>Použití debuggerbrowsableattribute –
 Použít <xref:System.Diagnostics.DebuggerBrowsableAttribute> pole nebo vlastnosti a určit, jak pole nebo vlastnost se zobrazí v okně ladicího programu. Konstruktor pro tento atribut má jednu z <xref:System.Diagnostics.DebuggerBrowsableState> hodnot výčtu, které určuje jeden z následujících stavů:

-   <xref:System.Diagnostics.DebuggerBrowsableState.Never> Označuje, že člen není zobrazen v okně data.  Například použití pro tuto hodnotu <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole odstraní pole z hierarchie; pole se nezobrazí, pokud rozšiřujete nadřazeného typu. Kliknutím na symbol plus (+) pro instanci typu.

-   <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> Označuje, že člen je zobrazen ale nebyla rozšířená. ve výchozím nastavení.  Toto je výchozí chování.

-   <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> Označuje, že samotný člen není zobrazen, ale jeho základní objektů se zobrazí, pokud je pole nebo kolekce.

> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> Nepodporuje Visual Basic v rozhraní .NET Framework verze 2.0.

Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> zabránit vlastnost následující povolí, v okně ladění pro třídu.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Použití DebuggerTypeProxy
 Použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atribut, když budete chtít v podstatě a výrazně změnit zobrazení ladění typu, ale nikoli změnit samotného typu. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut se používá k určení zobrazení proxy pro typ, povolení pro vývojáře pro přizpůsobení zobrazení typu.  Tento atribut, jako je třeba <xref:System.Diagnostics.DebuggerDisplayAttribute>, lze použít na úrovni sestavení, v takovém případě <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> vlastnost určuje typ, pro který se použije proxy server. Doporučuje, aby tento atribut určuje privátní vnořený typ, který se nachází v rámci typu, ke kterému se atribut používá.  Vyhodnocovače výrazů, podporuje typ kontroly prohlížeče pro tento atribut při zobrazení typu. Pokud se najde atribut vyhodnocovací filtr výrazů nahradí zobrazení proxy server, zadejte pro typ atributu se použije na.

 Když <xref:System.Diagnostics.DebuggerTypeProxyAttribute> je k dispozici, v okně proměnné ladicího programu se zobrazí pouze veřejné členy typ proxy serveru. Soukromé členy nejsou zobrazeny. Chování okna data se nemění podle atribut rozšířeného zobrazení.

 Aby se zabránilo snížení výkonu zbytečné, atributy proxy zobrazení nezpracovávají, dokud nebude objekt rozbalen, až uživatel kliknutím na symbol plus (+) vedle typ v okně data nebo prostřednictvím použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> atribut. Doporučujeme proto, že žádné atributy použít pro typ zobrazení. Atributy lze a bude použito v těle typ zobrazení.

 Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> zadat typ má být použit jako proxy server zobrazení ladicího programu.

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad kódu lze zobrazit v sadě Visual Studio zobrazíte výsledky použití <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, a <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atributy.

### <a name="code"></a>Kód

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>