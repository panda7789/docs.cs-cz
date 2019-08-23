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
ms.openlocfilehash: c27732de448e19c4227062706c7a7d73c98e5f19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966876"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Rozšíření ladění pomocí atributů zobrazení ladicího programu

Atributy zobrazení ladicího programu umožňují vývojáři typu, který určuje a nejlépe porozumět chování za běhu tohoto typu, k určení toho, jaký typ bude vypadat, jako by se zobrazil v ladicím programu. Kromě toho je možné atributy zobrazení ladicího programu `Target` , které poskytují vlastnost, použít na úrovni sestavení uživateli bez znalosti zdrojového kódu. <xref:System.Diagnostics.DebuggerDisplayAttribute> Atribut určuje, jak se typ nebo člen zobrazí v oknech proměnných ladicího programu. <xref:System.Diagnostics.DebuggerBrowsableAttribute> Atribut určuje, zda a jak se pole nebo vlastnost zobrazí v oknech proměnných ladicího programu. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut určuje náhradní typ nebo proxy, pro typ a mění způsob, jakým se typ zobrazuje v oknech ladicího programu. Pokud zobrazíte proměnnou, která má proxy, nebo náhradní typ, proxy se v okně zobrazí jako původní typ v okně zobrazení ladicího programu. Okno proměnné ladicího programu zobrazuje pouze veřejné členy typu proxy serveru. Soukromé členy nejsou zobrazeny.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Použití DebuggerDisplayAttribute –  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor má jeden argument: řetězec, který má být zobrazen ve sloupci value pro instance daného typu. Tento řetězec může obsahovat složené závorky ({a}). Text v páru složených závorek je vyhodnocen jako výraz. Například následující C# kód způsobí zobrazení "Count = 4", pokud je vybráno znaménko plus (+) pro rozšíření zobrazení ladicího programu pro instanci `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Atributy použité na vlastnosti odkazované ve výrazu nejsou zpracovány. Pro C# kompilátor je povolen obecný výraz, který má pouze implicitní přístup k tomuto odkazu pro aktuální instanci cílového typu. Výraz je omezený; není k dispozici žádný přístup k aliasům, místním hodnotám ani ukazatelům. V C# kódu můžete použít obecný výraz mezi složenými závorkami, které mají implicitní přístup k `this` ukazateli pouze pro aktuální instanci cílového typu.

Například pokud je C# objekt `ToString()`přepsaný, ladicí program zavolá přepsání a zobrazí jeho výsledek místo standardu `{<typeName>}.` , takže pokud jste přepsali `ToString()`, nemusíte používat <xref:System.Diagnostics.DebuggerDisplayAttribute>. Použijete-li obojí, <xref:System.Diagnostics.DebuggerDisplayAttribute> atribut má přednost `ToString()` před přepsáním.

## <a name="using-the-debuggerbrowsableattribute"></a>Použití DebuggerBrowsableAttribute
 <xref:System.Diagnostics.DebuggerBrowsableAttribute> Použijte pro pole nebo vlastnost k určení, jak se má pole nebo vlastnost zobrazovat v okně ladicího programu. Konstruktor pro tento atribut přebírá jednu z <xref:System.Diagnostics.DebuggerBrowsableState> hodnot výčtu, která určuje jeden z následujících stavů:

- <xref:System.Diagnostics.DebuggerBrowsableState.Never>indikuje, že člen není zobrazen v okně data.  Například při použití této hodnoty pro <xref:System.Diagnostics.DebuggerBrowsableAttribute> pole v poli dojde k odebrání pole z hierarchie; pole se nezobrazí, když rozbalíte nadřazený typ kliknutím na znaménko plus (+) pro instanci typu.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>indikuje, že se člen zobrazuje, ale ve výchozím nastavení není rozbalený.  Toto je výchozí chování.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>označuje, že samotný člen není zobrazen, ale jeho prvky jsou zobrazeny, pokud se jedná o pole nebo kolekci.

> [!NOTE]
> Služba <xref:System.Diagnostics.DebuggerBrowsableAttribute> není podporována Visual Basic v .NET Framework verze 2,0.

Následující příklad kódu ukazuje použití, <xref:System.Diagnostics.DebuggerBrowsableAttribute> aby se zabránilo tomu, aby se vlastnost po zobrazení v okně ladění pro třídu.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Použití používání DebuggerTypeProxy
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Použijte atribut, pokud potřebujete významně a v podstatě změnit zobrazení ladění typu, ale neměňte samotný typ. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut slouží k určení zobrazovaného proxy serveru pro určitý typ, který vývojářům umožňuje přizpůsobit zobrazení pro daný typ.  Tento atribut, jako je <xref:System.Diagnostics.DebuggerDisplayAttribute>, lze použít na úrovni sestavení, v takovém <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> případě vlastnost určuje typ, pro který bude použit proxy server. Doporučené použití je, že tento atribut určuje soukromý vnořený typ, který se vyskytuje v rámci typu, na který je atribut použit.  Vyhodnocovací filtr výrazů, který podporuje posluchače typu pro tento atribut při zobrazení typu. Pokud je atribut nalezen, vyhodnocení výrazu nahradí typ proxy zobrazení pro typ, na který je atribut použit.

 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Když je přítomen, okno proměnné ladicího programu zobrazí pouze veřejné členy typu proxy serveru. Soukromé členy nejsou zobrazeny. Chování okna data se v zobrazeních s rozšířenými atributy nemění.

 Aby nedocházelo k zbytečným sankcím, nezpracovává atributy zobrazovaného proxy serveru, dokud není objekt rozbalený, a to buď kliknutím na znaménko plus (+) vedle typu v okně dat, nebo prostřednictvím aplikace <xref:System.Diagnostics.DebuggerBrowsableAttribute> přidělen. Proto se doporučuje, aby se pro typ zobrazení nepoužívaly žádné atributy. Atributy mohou a by měly být aplikovány v těle typu zobrazení.

 Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> nástroje k určení typu, který se má použít jako proxy zobrazení ladicího programu.

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

Následující příklad kódu lze zobrazit v aplikaci Visual Studio pro zobrazení výsledků použití <xref:System.Diagnostics.DebuggerDisplayAttribute>atributů, <xref:System.Diagnostics.DebuggerBrowsableAttribute>a <xref:System.Diagnostics.DebuggerTypeProxyAttribute> .

### <a name="code"></a>Kód

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
