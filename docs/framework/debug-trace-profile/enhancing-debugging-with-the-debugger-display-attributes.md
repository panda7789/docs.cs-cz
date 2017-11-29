---
title: "Rozšíření ladění pomocí atributů zobrazení ladicího programu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c396a794cd3afa394cbb6b2393257a3103c6239d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Rozšíření ladění pomocí atributů zobrazení ladicího programu
Atributů zobrazení ladicího programu povolit vývojář typu, který určuje a nejlépe rozumí modul runtime chování tohoto typu, také určit, co daný typ bude vypadat, který se zobrazí v ladicí program. Kromě toho ladicí program atributy, které poskytují zobrazení `Target` vlastnost lze použít na úrovni sestavení uživatelé bez vědomí zdrojového kódu. <xref:System.Diagnostics.DebuggerDisplayAttribute> Atribut ovládací prvky zobrazení typ nebo člen v proměnnými ladicího programu. <xref:System.Diagnostics.DebuggerBrowsableAttribute> Atribut určuje, zda a jak pole nebo vlastnost je zobrazena v proměnnými ladicího programu. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut určuje typ substitute nebo proxy server, pro typ a mění způsob přidělování typ se zobrazí v ladicího programu. Při zobrazení proměnné, která má proxy server, nebo nahraďte typ proxy serveru znamená původní typ v okně zobrazení ladicího programu**.** Zadejte pouze veřejné členy proxy proměnné windowdisplays ladicí program. Soukromé členy nejsou zobrazeny.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Pomocí DebuggerDisplayAttribute  
 <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor má jeden argument: řetězec, který se zobrazí ve sloupci Hodnota pro instance typu. Tento řetězec může obsahovat složené závorky ({a}). Text v páru složených závorek je vyhodnoceno jako výraz. Například následující kód C# způsobí "Count = 4" na zobrazí, když je vybrán znaménko plus (+) rozbalte zobrazení ladicího programu pro instanci `MyHashtable`.  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 Atributy použité na vlastnosti odkazován ve výrazu nejsou předmětem zpracování. Pro kompilátor jazyka C# je povolen obecné výraz, který má jenom implicitní přístup na tento odkaz pro aktuální instancí třídy na typ cíle. Výraz je omezená; není k dispozici přístup k aliasy, místní hodnoty nebo ukazatele. V kódu jazyka C#, můžete použít výraz obecné mezi složené závorky, které má implicitní přístup k `this` ukazatele pro aktuální instancí třídy na typ cíle.  
  
 Například, pokud má objekt C# překryté `ToString()`, ladicí program zavolá přepsání a zobrazit její výsledek místo standardní `{<typeName>}.` zacílí, pokud mají přepsat `ToString()`, není potřeba použít <xref:System.Diagnostics.DebuggerDisplayAttribute>. Pokud používáte obě, <xref:System.Diagnostics.DebuggerDisplayAttribute> atribut má přednost před `ToString()` přepsat.  
  
## <a name="using-the-debuggerbrowsableattribute"></a>Pomocí debuggerbrowsableattribute –  
 Použít <xref:System.Diagnostics.DebuggerBrowsableAttribute> pole nebo vlastnost k určení, jak pole nebo vlastnost se zobrazí v okně ladicí program. V konstruktoru pro tento atribut má jednu z <xref:System.Diagnostics.DebuggerBrowsableState> hodnoty výčtu, které určuje jednu z následujících stavů:  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Never>Označuje, že člen není zobrazen v okně data.  Například pomocí této hodnoty pro <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole odebere pole z hierarchie; pole se nezobrazí, pokud rozbalíte kliknutím na symbol plus (+) pro instanci typu nadřazených typů.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>Označuje, že je člen zobrazí ale není rozšířit ve výchozím nastavení.  Toto je výchozí chování.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>Určuje, že člena samotného není vidět, ale pokud je pole nebo kolekce, zobrazí se jeho základní objekty.  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> Nepodporuje Visual Basic v rozhraní .NET Framework verze 2.0.  
  
 Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> aby vlastnost následující zobrazování v okně ladění pro třídu.  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a>Pomocí DebuggerTypeProxy  
 Použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Pokud budete potřebovat výrazně a zásadně změnit zobrazení ladění typu, ale neumožňuje změnit vlastní typ atributu. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut slouží k určení zobrazení proxy pro typ, což vývojáře k přizpůsobit zobrazení pro typ.  Tento atribut, jako je třeba <xref:System.Diagnostics.DebuggerDisplayAttribute>, lze použít na úrovni sestavení, v takovém případě <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> vlastnost určuje typ, pro který se použije k proxy serveru. Doporučené využití je, že tento atribut určuje privátní vnořené typy, který se vyskytuje v typu, na který se použije atribut.  Vyhodnocení výrazu, podporuje typ prohlížeče kontroluje pro tento atribut, když se zobrazí typu. Pokud je nalezen atribut, nahradí vyhodnocovací filtr výrazů zobrazení typ proxy pro typ atributu se použije na.  
  
 Když <xref:System.Diagnostics.DebuggerTypeProxyAttribute> je k dispozici, v okně proměnné ladicí program se zobrazí pouze veřejné členy typ proxy. Soukromé členy nejsou zobrazeny. Chování okna dat není změnit atribut rozšířeného zobrazení.  
  
 Aby nedošlo k penalizaci zbytečně výkon, nebudou zpracovány atributy zobrazení proxy, dokud objekt je rozšířena prostřednictvím uživatel kliknutím na symbol plus (+) vedle typu v okně data nebo prostřednictvím použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> atribut. Proto se doporučuje, aby se žádné atributy použijí na typ zobrazení. Atributy může a měla by se použít v textu typu zobrazení.  
  
 Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> k určení typu, který se má použít jako proxy server zobrazení ladicího programu.  
  
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
 Následující příklad kódu lze zobrazit v [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a zobrazte si výsledky použití <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, a <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atributy.  
  
### <a name="code"></a>Kód  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
