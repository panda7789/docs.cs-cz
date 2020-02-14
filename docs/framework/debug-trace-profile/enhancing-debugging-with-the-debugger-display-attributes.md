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
ms.openlocfilehash: ca118bffb045a0e7e3a5084916a0ff8020ebda90
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216496"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Rozšíření ladění pomocí atributů zobrazení ladicího programu

Atributy zobrazení ladicího programu umožňují vývojáři typu, který určuje a nejlépe porozumět chování za běhu tohoto typu, k určení toho, jaký typ bude vypadat, jako by se zobrazil v ladicím programu. Kromě toho mohou být atributy zobrazení ladicího programu, které poskytují vlastnost `Target`, na úrovni sestavení aplikovány uživateli bez znalosti zdrojového kódu. Atribut <xref:System.Diagnostics.DebuggerDisplayAttribute> určuje, jak se typ nebo člen zobrazí v oknech proměnných ladicího programu. Atribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> určuje, zda a jak se pole nebo vlastnost zobrazí v oknech proměnných ladicího programu. Atribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> určuje náhradní typ nebo proxy server pro typ a mění způsob, jakým se typ zobrazuje v oknech ladicího programu. Pokud zobrazíte proměnnou, která má proxy, nebo náhradní typ, proxy se v okně zobrazí jako původní typ v okně zobrazení ladicího programu. Okno proměnné ladicího programu zobrazuje pouze veřejné členy typu proxy serveru. Soukromé členy nejsou zobrazeny.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Použití DebuggerDisplayAttribute –  

Konstruktor <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> má jeden argument: řetězec, který se má zobrazit ve sloupci value pro instance daného typu. Tento řetězec může obsahovat složené závorky ({a}). Text v páru složených závorek je vyhodnocen jako výraz. Například následující C# kód způsobí zobrazení "Count = 4", pokud je vybráno znaménko plus (+) pro rozšíření zobrazení ladicího programu pro instanci `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Atributy použité na vlastnosti odkazované ve výrazu nejsou zpracovány. Pro C# kompilátor je povolen obecný výraz, který má pouze implicitní přístup k tomuto odkazu pro aktuální instanci cílového typu. Výraz je omezený; není k dispozici žádný přístup k aliasům, místním hodnotám ani ukazatelům. V C# kódu můžete použít obecný výraz mezi složenými závorkami, které mají implicitní přístup k ukazateli `this` pro aktuální instanci cílového typu.

Například pokud je C# objekt přepsaný `ToString()`, ladicí program bude volat přepsání a namísto standardního `{<typeName>}.` zobrazit jeho výsledek, takže pokud jste přepsali `ToString()`, nemusíte používat <xref:System.Diagnostics.DebuggerDisplayAttribute>. Použijete-li obojí, atribut <xref:System.Diagnostics.DebuggerDisplayAttribute> má přednost před přepsáním `ToString()`.

## <a name="using-the-debuggerbrowsableattribute"></a>Použití DebuggerBrowsableAttribute
 Použijte <xref:System.Diagnostics.DebuggerBrowsableAttribute> pro pole nebo vlastnost k určení, jak se má pole nebo vlastnost zobrazovat v okně ladicího programu. Konstruktor pro tento atribut přijímá jednu z <xref:System.Diagnostics.DebuggerBrowsableState> hodnot výčtu, která určuje jeden z následujících stavů:

- <xref:System.Diagnostics.DebuggerBrowsableState.Never> označuje, že člen není zobrazen v okně data.  Například použití této hodnoty pro <xref:System.Diagnostics.DebuggerBrowsableAttribute> v poli odebere pole z hierarchie; pole se nezobrazí, když rozbalíte nadřazený typ kliknutím na znaménko plus (+) pro instanci typu.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> označuje, že se člen zobrazuje, ale ve výchozím nastavení není rozbalený.  Toto je výchozí chování.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> označuje, že samotný člen není zobrazen, ale jeho prvky jsou zobrazeny, pokud se jedná o pole nebo kolekci.

> [!NOTE]
> <xref:System.Diagnostics.DebuggerBrowsableAttribute> není podporován Visual Basic v .NET Framework verzi 2,0.

Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerBrowsableAttribute>, aby se zabránilo tomu, aby se vlastnost po ní zobrazovala v okně ladění pro třídu.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Použití používání DebuggerTypeProxy
 Atribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> použijte v případě, že potřebujete významně a zásadním způsobem změnit zobrazení ladění typu, ale neměňte samotný typ. Atribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> slouží k určení zobrazovaného proxy serveru pro určitý typ, který vývojářům umožňuje přizpůsobit zobrazení pro daný typ.  Tento atribut, jako je <xref:System.Diagnostics.DebuggerDisplayAttribute>, lze použít na úrovni sestavení. v takovém případě vlastnost <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> určuje typ, pro který bude použit proxy server. Doporučené použití je, že tento atribut určuje soukromý vnořený typ, který se vyskytuje v rámci typu, na který je atribut použit.  Vyhodnocovací filtr výrazů, který podporuje posluchače typu pro tento atribut při zobrazení typu. Pokud je atribut nalezen, vyhodnocení výrazu nahradí typ proxy zobrazení pro typ, na který je atribut použit.

 Pokud je k dispozici <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, okno proměnné ladicího programu zobrazí pouze veřejné členy typu proxy serveru. Soukromé členy nejsou zobrazeny. Chování okna data se v zobrazeních s rozšířenými atributy nemění.

 Aby nedocházelo k zbytečnému vlivu na výkon, atributy zobrazení proxy nejsou zpracovány, dokud není objekt rozbalen, a to buď po kliknutí na znaménko plus (+) vedle typu v okně dat, nebo prostřednictvím aplikace atributu <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Proto se doporučuje, aby se pro typ zobrazení nepoužívaly žádné atributy. Atributy mohou a by měly být aplikovány v těle typu zobrazení.

 Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> k určení typu, který se má použít jako proxy zobrazení ladicího programu.

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

Následující příklad kódu lze zobrazit v aplikaci Visual Studio pro zobrazení výsledků použití atributů <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>a <xref:System.Diagnostics.DebuggerTypeProxyAttribute>.

### <a name="code"></a>Kód

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
