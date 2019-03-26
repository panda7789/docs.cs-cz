---
title: Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ca8cf76745190bd9819dde522c34e57952cd1ca
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410456"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)

Direktivy modulu runtime (. rd.xml) soubor je konfigurační soubor XML, který určuje, zda jsou k dispozici pro účely reflexe prvky určené programu. Tady je příklad souboru direktiv modulu runtime:

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
<Application>
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />

  <Namespace Name="System.Collections.ObjectModel" >
    <TypeInstantiation Name="ObservableCollection"
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />
    <TypeInstantiation Name="ReadOnlyObservableCollection"
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />
  </Namespace>
</Application>
</Directives>
```

## <a name="the-structure-of-a-runtime-directives-file"></a>Struktura souboru direktiv modulu runtime

Direktivy modulu runtime souboru používá `http://schemas.microsoft.com/netfx/2013/01/metadata` oboru názvů.

Kořenový prvek je [direktivy](../../../docs/framework/net-native/directives-element-net-native.md) elementu. Může obsahovat nula nebo více [knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementy a nula nebo jedna [aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu, jak je znázorněno v následující strukturu. Atributy [aplikace](../../../docs/framework/net-native/application-element-net-native.md) element můžete definovat zásady reflexe modulu runtime celou aplikaci, nebo může sloužit jako kontejner pro podřízené prvky. [Knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementu, na druhé straně je prostě kontejner. Podřízené objekty daného [aplikace](../../../docs/framework/net-native/application-element-net-native.md) a [knihovny](../../../docs/framework/net-native/library-element-net-native.md) elementy definovat typy, metody, pole, vlastnosti a události, které jsou k dispozici pro účely reflexe.

Referenční informace, zvolte prvky z následující strukturu nebo naleznete v tématu [elementy direktivy modulu Runtime](../../../docs/framework/net-native/runtime-directive-elements.md). V následující hierarchie označí se třemi tečkami rekurzivní strukturou. Informace v závorkách označují, jestli tento element je nepovinné nebo povinné, a pokud se používá, kolik instancí (jeden nebo více) jsou povoleny.

[Direktivy](../../../docs/framework/net-native/directives-element-net-native.md) [1:1] [aplikace](../../../docs/framework/net-native/application-element-net-native.md) [0:1] [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M] [podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy nadřazeného typu) [O:1] [typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atributem) [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M] [ TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (vytvořený obecnou metodu) [0:M] [vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [Pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [události](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M] [typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [parametr](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M] [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) () Vytvořit obecnou metodu) [0:M] [vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [události](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [knihovny](../../../docs/framework/net-native/library-element-net-native.md) [0:M] [Sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M] [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[Typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M] [podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md) (podtřídy nadřazeného typu) [O:1] [typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (obsahující typ je atributem) [O:1] [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M] [metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (Konstruovaný obecný Metoda) [0:M] [vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [události](../../../docs/framework/net-native/event-element-net-native.md) [0:M] [TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0: M] [typ](../../../docs/framework/net-native/type-element-net-native.md) [0:M]. . .
[TypeInstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (Konstruovaný obecný typ) [0:M]. . .
[Metoda](../../../docs/framework/net-native/method-element-net-native.md) [0:M] [MethodInstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (vytvořený obecnou metodu) [0:M] [vlastnost](../../../docs/framework/net-native/property-element-net-native.md) [0:M] [pole](../../../docs/framework/net-native/field-element-net-native.md) [0:M] [události](../../../docs/framework/net-native/event-element-net-native.md)[0:M]

[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) prvek může mít žádné atributy, nebo může mít atributy zásad popsané v [Runtime směrnice a zásady části](#Directives).

A [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element má jeden atribut `Name`, který určuje název knihovny nebo bez jeho přípona souboru sestavení. Například následující [knihovny](../../../docs/framework/net-native/library-element-net-native.md) element se vztahuje na sestavení s názvem Extensions.dll.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
  <Application>
     <!-- Child elements go here -->
  </Application>
  <Library Name="Extensions">
     <!-- Child elements go here -->
  </Library>
</Directives>
```

<a name="Directives"></a>

## <a name="runtime-directives-and-policy"></a>Direktivy modulu runtime a zásady

[Aplikace](../../../docs/framework/net-native/application-element-net-native.md) elementu samotného a podřízených elementů [knihovny](../../../docs/framework/net-native/library-element-net-native.md) a [aplikace](../../../docs/framework/net-native/application-element-net-native.md) prvky vyjádření zásad; to znamená, že definují způsob, ve kterém můžete použít aplikaci reflexe pro prvek programu. Typ zásad je definován atribut prvku (například `Serialize`). Hodnota zásad je definována hodnota atributu (například `Serialize="Required"`).

Všechny zásady určené atribut elementu se vztahuje na všechny podřízené prvky, které nechcete zadat hodnotu pro tuto zásadu. Například, pokud je zásada určená [typ](../../../docs/framework/net-native/type-element-net-native.md) elementu, které zásady platí pro všechny typy a členy, u kterých není explicitně zadán zásadu.

Zásady, které lze vyjádřit pomocí [aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md), a [typ](../../../docs/framework/net-native/type-element-net-native.md) prvky se liší od zásad, který může být vyjádřena pro jednotlivé členy (podle [metoda](../../../docs/framework/net-native/method-element-net-native.md), [vlastnost](../../../docs/framework/net-native/property-element-net-native.md), [Pole](../../../docs/framework/net-native/field-element-net-native.md), a [události](../../../docs/framework/net-native/event-element-net-native.md) elementy).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Určení zásad pro sestavení, oborů názvů a typy

[Aplikace](../../../docs/framework/net-native/application-element-net-native.md), [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md), [AttributeImplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [podtypy](../../../docs/framework/net-native/subtypes-element-net-native.md)a [ Typ](../../../docs/framework/net-native/type-element-net-native.md) prvky podporu následujících typů zásad:

- `Activate`. Řídí přístup runtime konstruktorů, umožňuje aktivaci instancí.

- `Browse`. Ovládací prvky, zadávání dotazů na informace o prvcích program, ale neumožňuje přístup modulu runtime.

- `Dynamic`. Ovládací prvky přístupu modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování.

- `Serialize`. Řídí přístup k modulu runtime pro konstruktory, polí a vlastností, aby instance typu být serializován a serializováno modulem knihovny třetích stran, jako je například serializátor Newtonsoft JSON.

- `DataContractSerializer`. Určuje zásady pro serializaci, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.

- `DataContractJsonSerializer`. Určuje zásady pro serializaci JSON, který používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídy.

- `XmlSerializer`. Určuje zásady pro serializaci kódu XML, který používá <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídy.

- `MarshalObject`. Určuje zásady pro zařazování typy odkazů ve WinRT a COM.

- `MarshalDelegate`. Určuje zásady pro zařazování typy delegátů jako ukazatelů na funkce do nativního kódu.

- `MarshalStructure` . Určuje zásady pro zařazování struktur do nativního kódu.

Nastavení související s těmito typy zásad jsou:

- `All`. Povolte zásady pro všechny typy a členy, které řetězce nástrojů se neodeberou.

- `Auto`. Použije výchozí chování. (Zásady bez zadání je ekvivalentní k nastavení této zásady na `Auto` Pokud tuto zásadu je přepsána, například nadřazeného elementu.)

- `Excluded`. Zásada pro ovládací prvek programu.

- `Public`. Povolte zásady pro veřejné typy nebo členy, pokud řetězec nástrojů zjistí, že člen není nutný a proto ji odebere. (V druhém případě je nutné použít `Required Public` zajistíte, že člen je uložen a má schopnosti reflexe.)

- `PublicAndInternal`. Povolte zásady pro veřejné a vnitřní typy nebo členy, pokud řetězec nástrojů neodebere.

- `Required Public`. Vyžadovat řetězce nástrojů se veřejné typy a členy, které určuje, jestli se používají a povolte zásady pro ně.

- `Required PublicAndInternal`. Vyžadovat řetězce nástrojů se veřejné a vnitřní typy a členy, které určuje, jestli se používají a povolte zásady pro ně.

- `Required All`. Vyžadují řetězce nástrojů zachovat všechny typy a členy, které určuje, jestli se používají a povolte zásady pro ně.

Například následující soubor direktiv modulu runtime definuje zásady pro všechny typy a členy v sestavení DataClasses.dll. Umožňuje reflexe pro serializaci všechny veřejné vlastnosti, umožňuje procházení pro všechny typy a členy typu, umožňuje aktivaci pro všechny typy (z důvodu `Dynamic` atribut) a umožňuje reflexe pro všechny veřejné typy a členy.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"
                Browse="All" Activate="PublicAndInternal"
                Dynamic="Public"  />
   </Application>
   <Library Name="UtilityLibrary">
     <!-- Child elements go here -->
   </Library>
</Directives>
```

### <a name="specifying-policy-for-members"></a>Určení zásad pro členy

[Vlastnost](../../../docs/framework/net-native/property-element-net-native.md) a [pole](../../../docs/framework/net-native/field-element-net-native.md) prvky podporu následujících typů zásad:

- `Browse` – Ovládací prvky dotazování na informace o tomto členu, ale neumožňuje přístup modulu runtime.

- `Dynamic` -Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování. Určuje také dotazování na informace o nadřazeném typu.

- `Serialize` -Určuje runtime přístup k členu instance typu k serializaci a deserializaci knihovnami, jako je například serializátor Newtonsoft JSON povolit. Tuto zásadu lze použít pro konstruktory, polí a vlastností.

[Metoda](../../../docs/framework/net-native/method-element-net-native.md) a [události](../../../docs/framework/net-native/event-element-net-native.md) prvky podporu následujících typů zásad:

- `Browse` – Ovládací prvky dotazování na informace o tomto členu, ale neumožňuje přístup modulu runtime.

- `Dynamic` -Řídí přístup k modulu runtime pro všechny členy typu, včetně konstruktorů, metod, pole, vlastnosti a události, chcete povolit dynamické programování. Určuje také dotazování na informace o nadřazeném typu.

 Nastavení související s těmito typy zásad jsou:

- `Auto` – Použijte výchozí chování. (Zásady bez zadání je ekvivalentní k nastavení této zásady na `Auto` Pokud něco ji přepisuje.)

- `Excluded` -Nikdy Nezahrnovat metadata pro tohoto člena.

- `Included` -Zásadu povolte, pokud je k dispozici ve výstupu nadřazeného typu.

- `Required` -Vyžaduje řetězec nástrojů zachovat tento člen se zobrazí i v případě nevyužitá a povolte zásady pro něj.

## <a name="runtime-directives-file-semantics"></a>Sémantika souboru direktiv modulu runtime

Zásady lze definovat současně pro elementy vyšší úrovně a nižší úrovně. Zásady lze například definovat pro sestavení a pro některé typy obsažené v tomto sestavení. Pokud není zastoupen konkrétní element nižší úrovně, zdědí zásada svého nadřazeného objektu. Například pokud `Assembly` element je k dispozici, ale `Type` prvky nejsou, zásady zadaná v `Assembly` element platí pro jednotlivé typy v sestavení. Více prvků lze také použít zásady stejný ovládací prvek programu. Například samostatné [sestavení](../../../docs/framework/net-native/assembly-element-net-native.md) elementy definovat stejný element zásad pro stejného sestavení odlišně. Následující části popisují, jak zásady pro konkrétní typ vyřeší v těchto případech.

A [typ](../../../docs/framework/net-native/type-element-net-native.md) nebo [metoda](../../../docs/framework/net-native/method-element-net-native.md) element obecného typu nebo metody své zásady platí pro všechny instance, nesmí být svými vlastními zásadami. Například `Type` prvek, který určuje zásady pro <xref:System.Collections.Generic.List%601> nepřepíšete pro konkrétní Konstruovaný obecný typ se vztahuje na všechny instance Konstruovaný obecný typ, (, jako `List<Int32>`) podle `TypeInstantiation` elementu. V opačném případě elementy definovat zásady pro ovládací prvek programu s názvem.

Pokud element je nejednoznačný, modul hledá shody a pokud se najde přesná shoda, použije ji. Pokud se najde více shod, bude upozornění nebo chyby.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Pokud dvě direktivy uplatňovat zásady na stejný ovládací prvek programu

Pokud dva prvky v různých běhových direktivy souborů došlo k pokusu o nastavení stejného typu zásady pro stejný ovládací prvek programu (například sestavení nebo typ) na různé hodnoty, je konflikt vyřešen následujícím způsobem:

1. Pokud `Excluded` element je k dispozici, má přednost.

2. `Required` má vyšší prioritu více not `Required`.

3. `All` má vyšší prioritu než `PublicAndInternal`, který má vyšší prioritu než `Public`.

4. Žádné explicitní nastavení má vyšší prioritu než `Auto`.

Například, pokud jeden projekt obsahuje následující dva soubory direktivy modulu runtime, serializace pro DataClasses.dll je zásada nastavená na obojí `Required Public` a `All`. V takovém případě bude vyřešeno jako zásady serializace `Required All`.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public"/>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="All" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

Pokud dvě direktivy v souboru direktivy jeden modul runtime došlo k pokusu o nastavení stejného typu zásady pro stejný ovládací prvek programu, ale nástroj definici schématu XML zobrazí chybovou zprávu.

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Když použijete podřízenými a nadřazenými prvky stejného typu zásad

Podřízené prvky přepsat jejich nadřazených prvků, včetně `Excluded` nastavení. Přepsání je hlavní důvod, proč byste měli určit `Auto`.

V následujícím příkladu, nastavení pro všechno, co v zásady serializace `DataClasses` , který není v `DataClasses.ViewModels` by `Required Public`a vše, co je v obou `DataClasses` a `DataClasses.ViewModels` by `All`.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Pokud otevřete obecné typy a instance prvky použití stejného typu zásad

V následujícím příkladu `Dictionary<int,int>` je přiřazen `Browse` zásad jenom v případě, že modul je dalším důvodem pro ni `Browse` zásady (které by jinak byly výchozí chování); všechny další instance <xref:System.Collections.Generic.Dictionary%602> budou mít všechny jejích členů nelze procházet.

```xml
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">
   <Application>
      <Assembly Name="DataClasses" Serialize="Required Public" >
         <Namespace Name="DataClasses.ViewModels" Serialize="All" />
      </Assembly>
      <Namespace Name="DataClasses.Generics" />
      <Type Name="Dictionary" Browse="All" />
      <TypeInstantiation Name="Dictionary"
                         Arguments="System.Int32,System.Int32" Browse="Auto" />
   </Application>
   <Library Name="DataClasses">
      <!-- any other elements -->
   </Library>
</Directives>
```

### <a name="how-policy-is-inferred"></a>Jak odvodit zásad

Každý typ zásad má jinou sadu pravidel, které určují, jak ovlivňuje jiných objektů, které přítomnosti tohoto typu zásad.

#### <a name="the-effect-of-browse-policy"></a>Účinek zásady procházení

Použití `Browse` zásadu k typu zahrnuje následující změny zásad:

- Je označené základní typ typu `Browse` zásad.

- Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Browse` zásad.

- Pokud je typ delegáta `Invoke` metoda v typu je označena `Dynamic` zásad.

- Každé rozhraní typ je označen `Browse` zásad.

- Typ každého atributu použitý pro typ je označen pomocí `Browse` zásad.

- Pokud je typ obecný, je označené každého typu omezení `Browse` zásad.

- Pokud je typ obecný, typy, po které je vytvořena instance typu jsou označené `Browse` zásad.

Použití `Browse` zásad na metodu zahrnuje následující změny zásad:

- Každý typ parametru metody, je označené `Browse` zásad.

- Návratový typ metody je označené `Browse` zásad.

- Nadřazený typ metody je označené `Browse` zásad.

- Pokud je metoda vytvořenou instanci obecné metody, nevytvořeným instancím obecná metoda je označena `Browse` zásad.

- Typ každý atribut do metody je označené `Browse` zásad.

- Pokud je obecná metoda, je označené každého typu omezení `Browse` zásad.

- Pokud metody je obecný, typy, po které je vytvořena instance metoda jsou označeny `Browse` zásad.

Použití `Browse` zásad pole zahrnuje následující změny zásad:

- Typ každý atribut použit na pole je označeno `Browse` zásad.

- Typ pole je označeno `Browse` zásad.

- Typ, ke kterému patří toto pole je označeno `Browse` zásad.

#### <a name="the-effect-of-dynamic-policy"></a>Účinek zásady dynamického

Použití `Dynamic` zásadu k typu zahrnuje následující změny zásad:

- Je označené základní typ typu `Dynamic` zásad.

- Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Dynamic` zásad.

- Pokud typ je typ delegátu, `Invoke` metoda v typu je označena `Dynamic` zásad.

- Každé rozhraní typ je označen `Browse` zásad.

- Typ každého atributu použitý pro typ je označen pomocí `Browse` zásad.

- Pokud je typ obecný, je označené každého typu omezení `Browse` zásad.

- Pokud je typ obecný, typy, po které je vytvořena instance typu jsou označené `Browse` zásad.

Použití `Dynamic` zásad na metodu zahrnuje následující změny zásad:

- Každý typ parametru metody, je označené `Browse` zásad.

- Návratový typ metody je označené `Dynamic` zásad.

- Nadřazený typ metody je označené `Dynamic` zásad.

- Pokud je metoda vytvořenou instanci obecné metody, nevytvořeným instancím obecná metoda je označena `Browse` zásad.

- Typ každý atribut do metody je označené `Browse` zásad.

- Pokud je obecná metoda, je označené každého typu omezení `Browse` zásad.

- Pokud metody je obecný, typy, po které je vytvořena instance metoda jsou označeny `Browse` zásad.

- Metodu lze vyvolat pomocí `MethodInfo.Invoke`, a vytvoření delegáta je možné podle <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.

Použití `Dynamic` zásad pole zahrnuje následující změny zásad:

- Typ každý atribut použit na pole je označeno `Browse` zásad.

- Typ pole je označeno `Dynamic` zásad.

- Typ, ke kterému patří toto pole je označeno `Dynamic` zásad.

#### <a name="the-effect-of-activation-policy"></a>Účinek Zásady aktivace

Použití zásady aktivace do typu zahrnuje následující změny zásad:

- Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Browse` zásad.

- Pokud typ je typ delegátu, `Invoke` metoda v typu je označena `Dynamic` zásad.

- Konstruktory typu jsou označené `Activation` zásad.

Použití `Activation` zásad na metodu zahrnuje následující změnu zásad:

- Konstruktor jde vyvolat <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> a <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metody. Pro metody `Activation` zásada ovlivňuje pouze konstruktory.

Použití `Activation` zásad na pole nemá žádný vliv.

#### <a name="the-effect-of-serialize-policy"></a>Účinek zásady serializace

`Serialize` Zásad umožňuje použít běžné serializátory založenými na reflexi. Ale vzhledem k tomu, že se mají Microsoftu známé vzorce přístupů k přesný odraz serializátory od jiných výrobců, tyto zásady nemusí být zcela efektivní.

Použití `Serialize` zásadu k typu zahrnuje následující změny zásad:

- Je označené základní typ typu `Serialize` zásad.

- Pokud je instance obecný typ, je označena verze nevytvořeným instancím typu `Browse` zásad.

- Pokud typ je typ delegátu, `Invoke` metoda v typu je označena `Dynamic` zásad.

- Pokud je typ výčtu, je označené pole typu `Serialize` zásad.

- Pokud tento typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` je označené `Serialize` zásad.

- Pokud je typ <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, nebo <xref:System.Collections.Generic.IReadOnlyList%601>, pak `T[]` a <xref:System.Collections.Generic.List%601> označené `Serialize` zásad., ale žádné členy typu rozhraní jsou označené `Serialize`zásad.

- Pokud je typ <xref:System.Collections.Generic.List%601>, jsou označeny žádné členy typu `Serialize` zásad.

- Pokud je typ <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> je označené `Serialize` zásad. ale jsou označené žádné členy typu `Serialize` zásad.

- Pokud je typ <xref:System.Collections.Generic.Dictionary%602>, jsou označeny žádné členy typu `Serialize` zásad.

- Pokud tento typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` a `TValue` jsou označené `Serialize` zásad.

- Každý konstruktoru, každý přistupující objekt vlastnosti a každé pole je označeno `Serialize` zásad.

Použití `Serialize` zásad na metodu zahrnuje následující změny zásad:

- Nadřazený typ je označen `Serialize` zásad.

- Návratový typ metody je označené `Serialize` zásad.

Použití `Serialize` zásad pole zahrnuje následující změny zásad:

- Nadřazený typ je označen `Serialize` zásad.

- Typ pole je označeno `Serialize` zásad.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>Účinek zásady XmlSerializer, Třída DataContractSerializer a DataContractJsonSerializer

Na rozdíl od `Serialize` zásad, která je určena pro serializátory založenými na reflexi, <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>, a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> zásady slouží k povolení sadu serializátory, které jsou známé [!INCLUDE[net_native](../../../includes/net-native-md.md)] nástroj řetězce. Tyto serializátory nejsou implementované pomocí reflexe, ale sadu typů, které lze serializovat v době běhu je určen podobným způsobem jako typy, které jsou reflektovatelné.

Použít některou z těchto zásad do typu umožňuje, aby typ k serializaci pomocí serializátoru odpovídající. Navíc všechny typy, které potřebují serializace staticky určit Serializační stroj se také být serializovatelný.

Tyto zásady nemají žádný vliv na metody nebo pole.

Další informace najdete v části "Rozdíly v Serializátory" v [migrace Windows Store aplikace pro .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Viz také:

- [Elementy direktivy modulu runtime](../../../docs/framework/net-native/runtime-directive-elements.md)
- [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
