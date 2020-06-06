---
title: Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "76738405"
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)

Soubor direktiv modulu runtime (. Rd. XML) je konfigurační soubor XML, který určuje, zda jsou určené prvky programu k dispozici pro reflexi. Tady je příklad souboru direktiv modulu runtime:

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

Soubor direktiv modulu runtime používá `http://schemas.microsoft.com/netfx/2013/01/metadata` obor názvů.

Kořenový element je element [direktivy](directives-element-net-native.md) . Může obsahovat nula nebo více prvků [knihovny](library-element-net-native.md) a nula nebo jeden prvek [aplikace](application-element-net-native.md) , jak je znázorněno v následující struktuře. Atributy prvku [aplikace](application-element-net-native.md) mohou definovat zásady reflexe modulu runtime v rámci aplikace nebo mohou sloužit jako kontejner pro podřízené prvky. Element [Library (knihovna](library-element-net-native.md) ) je na druhé straně jednoduchý kontejner. Podřízené položky prvků [aplikace](application-element-net-native.md) a [knihovny](library-element-net-native.md) definují typy, metody, pole, vlastnosti a události, které jsou k dispozici pro reflexi.

Pro referenční informace vyberte prvky z následující struktury nebo si prohlédněte [elementy direktivy modulu runtime](runtime-directive-elements.md). V následující hierarchii se tři tečky označí rekurzivní strukturu. Informace v závorkách označují, zda je tento prvek volitelný nebo vyžadovaný, a pokud je použit, kolik instancí (jedna nebo mnoho) je povoleno.

- [Direktivy](directives-element-net-native.md) [1:1]
  - [Aplikace](application-element-net-native.md) [0:1]
    - [Sestavení](assembly-element-net-native.md) [0: M]
      - [Obor názvů](namespace-element-net-native.md) [0: M]. . .
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
    - [Obor názvů](namespace-element-net-native.md) [0: M]
      - [Obor názvů](namespace-element-net-native.md) [0: M]. . .
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
    - [Typ](type-element-net-native.md) [0: M]
      - [Podtypy](subtypes-element-net-native.md) (podtřídy obsahujícího typu) [O:1]
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
      - [AttributeImplies](attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]
      - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [Metoda](method-element-net-native.md) [0: M]
        - [Parametr](parameter-element-net-native.md) [0: M]
        - [TypeParameter](typeparameter-element-net-native.md) [0: M]
        - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]
      - [Vlastnost](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Událost](event-element-net-native.md) [0: M]
    - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
      - [Metoda](method-element-net-native.md) [0: M]
        - [Parametr](parameter-element-net-native.md) [0: M]
        - [TypeParameter](typeparameter-element-net-native.md) [0: M]
        - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]
      - [Vlastnost](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Událost](event-element-net-native.md) [0: M]
  - [Knihovna](library-element-net-native.md) [0: M]
    - [Sestavení](assembly-element-net-native.md) [0: M]
      - [Obor názvů](namespace-element-net-native.md) [0: M]. . .
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
    - [Obor názvů](namespace-element-net-native.md) [0: M]
      - [Obor názvů](namespace-element-net-native.md) [0: M]. . .
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
    - [Typ](type-element-net-native.md) [0: M]
      - [Podtypy](subtypes-element-net-native.md) (podtřídy obsahujícího typu) [O:1]
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
      - [AttributeImplies](attributeimplies-element-net-native.md) (obsahující typ je atribut) [O:1]
      - [GenericParameter](genericparameter-element-net-native.md) [0: M]
      - [Metoda](method-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]
      - [Vlastnost](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Událost](event-element-net-native.md) [0: M]
    - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]
      - [Zadejte](type-element-net-native.md) [0: M]. . .
      - [TypeInstantiation](typeinstantiation-element-net-native.md) (konstruovaný obecný typ) [0: M]. . .
      - [Metoda](method-element-net-native.md) [0: M]
      - [MethodInstantiation](methodinstantiation-element-net-native.md) (konstruované obecné metody) [0: M]
      - [Vlastnost](property-element-net-native.md) [0: M]
      - [Pole](field-element-net-native.md) [0: M]
      - [Událost](event-element-net-native.md) [0: M]

Element [aplikace](application-element-net-native.md) nemůže mít žádné atributy, nebo může mít atributy zásad popsané v [části direktiva a zásady modulu runtime](#Directives).

Element [knihovny](library-element-net-native.md) má jediný atribut, `Name` , který určuje název knihovny nebo sestavení bez přípony souboru. Například následující prvek [knihovny](library-element-net-native.md) se vztahuje na sestavení s názvem Extensions. dll.

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

## <a name="runtime-directives-and-policy"></a>Direktivy a zásady modulu runtime

Samotný prvek [aplikace](application-element-net-native.md) a podřízené prvky [knihovny](library-element-net-native.md) a prvků [aplikace](application-element-net-native.md) expresní zásady; To znamená, že definují způsob, jakým může aplikace použít reflexi u prvku programu. Typ zásady je definován atributem elementu (například `Serialize` ). Hodnota zásady je definována hodnotou atributu (například `Serialize="Required"` ).

Všechny zásady určené atributem elementu se vztahují na všechny podřízené prvky, které neurčují hodnotu pro tuto zásadu. Například pokud je zásada určena prvkem [typu](type-element-net-native.md) , tato zásada platí pro všechny obsažené typy a členy, pro které není explicitně určena zásada.

Zásady, které může vyjádřit [aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) , se liší od zásad, které je možné vyjádřit pro jednotlivé členy ( [metodou](method-element-net-native.md), [vlastností](property-element-net-native.md), [polem](field-element-net-native.md)a [událostmi](event-element-net-native.md) ).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Určení zásad pro sestavení, obory názvů a typy

[Aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) podporují následující typy zásad:

- `Activate`. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.

- `Browse`. Řídí dotazování pro informace o prvcích programu, ale neumožňuje přístup k modulu runtime.

- `Dynamic`. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.

- `Serialize`. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a serializovat pomocí knihoven třetích stran, jako je například serializátor Newtonsoft JSON.

- `DataContractSerializer`. Řídí zásady pro serializaci, která používá <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídu.

- `DataContractJsonSerializer`. Řídí zásady pro serializaci JSON, které používají <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> třídu.

- `XmlSerializer`. Řídí zásady pro serializaci XML, které používají <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> třídu.

- `MarshalObject`. Řídí zásady pro zařazování typů odkazů do WinRT a COM.

- `MarshalDelegate`. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.

- `MarshalStructure` . Řídí zásady pro zařazování struktur do nativního kódu.

Nastavení přidružená k těmto typům zásad jsou:

- `All`. Povolte zásadu pro všechny typy a členy, které řetěz nástroje neodebere.

- `Auto`. Použijte výchozí chování. (Není-li určena zásada, je rovnocenná nastavení zásad, `Auto` Pokud tato zásada není přepsána, například nadřazeným prvkem.)

- `Excluded`. Zakáže zásady pro prvek programu.

- `Public`. Povolte zásadu pro veřejné typy nebo členy, pokud řetěz nástrojů nezjistí, že je člen zbytečný a proto jej odebere. (V druhém případě je nutné použít, `Required Public` Chcete-li zajistit, že je člen udržován a má možnosti reflexe.)

- `PublicAndInternal`. Povolte zásady pro veřejné a interní typy nebo členy, pokud je řetěz nástrojů neodebere.

- `Required Public`. Vyžaduje, aby řetěz nástrojů zachoval veřejné typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.

- `Required PublicAndInternal`. Vyžaduje, aby řetěz nástrojů zachoval veřejné i interní typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.

- `Required All`. Vyžaduje, aby řetězec nástroje zachoval všechny typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.

Například následující direktivy modulu runtime definují zásadu pro všechny typy a členy v souboru DataClasses. dll sestavení. Umožňuje reflexi pro serializaci všech veřejných vlastností, umožňuje procházení pro všechny typy a členy typu, povoluje aktivaci pro všechny typy (z důvodu `Dynamic` atributu) a povoluje reflexi pro všechny veřejné typy a členy.

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

Prvky [Property](property-element-net-native.md) a [Field](field-element-net-native.md) podporují následující typy zásad:

- `Browse`– Řídí dotazování pro informace o tomto členu, ale neumožňuje přístup k modulu runtime.

- `Dynamic`– Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování. Také ovládá dotazování na informace o nadřazeného typu.

- `Serialize`– Řídí přístup k členu za běhu, aby se mohly instance typů serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor. Tuto zásadu lze použít na konstruktory, pole a vlastnosti.

[Metoda](method-element-net-native.md) a prvky [události](event-element-net-native.md) podporují následující typy zásad:

- `Browse`– Řídí dotazování pro informace o tomto členu, ale nepovoluje přístup za běhu.

- `Dynamic`– Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování. Také ovládá dotazování na informace o nadřazeného typu.

 Nastavení přidružená k těmto typům zásad jsou:

- `Auto`– Použije výchozí chování. (Není-li zadáno, zásada je ekvivalentní k nastavení této zásady, `Auto` Pokud ji nepřepisuje.)

- `Excluded`– Nikdy Nezahrnovat metadata pro člena.

- `Included`– Povolí zásadu, pokud se ve výstupu nachází nadřazený typ.

- `Required`– Vyžaduje, aby řetěz nástrojů zachoval tento člen, i když se zdá být nepoužitý, a pro něj povolí zásady.

## <a name="runtime-directives-file-semantics"></a>Sémantika souboru direktiv modulu runtime

Zásady lze definovat současně pro elementy vyšší úrovně i na nižší úrovni. Například zásada může být definována pro sestavení a pro některé typy obsažené v tomto sestavení. Pokud není určitý element na nižší úrovni reprezentován, zdědí zásady jeho nadřazeného objektu. Například pokud `Assembly` je prvek přítomen, ale prvky nejsou `Type` , zásady zadané v `Assembly` elementu se vztahují na každý typ v sestavení. U stejného prvku programu lze také použít více prvků. Například samostatné prvky [sestavení](assembly-element-net-native.md) mohou definovat stejný prvek zásad pro stejné sestavení odlišně. V následujících částech se dozvíte, jak se v těchto případech vyřeší zásada pro konkrétní typ.

[Typ](type-element-net-native.md) nebo prvek [metody](method-element-net-native.md) obecného typu nebo metody aplikuje zásady na všechny instance, které nemají vlastní zásady. Například `Type` element, který určuje zásadu pro <xref:System.Collections.Generic.List%601> , platí pro všechny vytvořené instance tohoto obecného typu, pokud není přepsán pro konkrétní konstruovaný typ (například a `List<Int32>` ) pomocí `TypeInstantiation` prvku. V opačném případě elementy definují zásady pro prvek program s názvem.

Pokud je prvek dvojznačný, modul hledá shody a pokud najde přesnou shodu, bude ho používat. Pokud najde více shod, dojde k upozornění nebo chybě.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Pokud dvě direktivy používají zásady na stejný prvek programu

Pokud se dva prvky v různých souborech běhových direktiv pokusí nastavit stejný typ zásad pro stejný prvek programu (například sestavení nebo typ) na jiné hodnoty, konflikt je vyřešen následujícím způsobem:

1. Pokud `Excluded` je prvek přítomen, má přednost.

2. `Required`má přednost před `Required` ne.

3. `All`má přednost před `PublicAndInternal` , která má přednost před `Public` .

4. Jakékoli explicitní nastavení má přednost před `Auto` .

Například pokud jeden projekt obsahuje následující dva soubory běhových direktiv, zásada serializace pro DataClasses. dll je nastavena na hodnotu `Required Public` a `All` . V takovém případě by zásada serializace byla vyřešena jako `Required All` .

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

Nicméně pokud se dvě direktivy v jednom souboru direktiv modulu runtime pokusí nastavit stejný typ zásad pro stejný prvek programu, nástroj definice schématu XML zobrazí chybovou zprávu.

### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Pokud podřízené a nadřazené prvky použijí stejný typ zásad

Podřízené prvky přepíšou své nadřazené prvky, včetně `Excluded` nastavení. Přepsání je hlavní důvod, který byste chtěli zadat `Auto` .

V následujícím příkladu nastavení zásad serializace pro všechno v `DataClasses` , které není v, `DataClasses.ViewModels` by bylo `Required Public` a všechno, co je v obou `DataClasses` i i `DataClasses.ViewModels` `All` .

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

### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Pokud jsou otevřené generické prvky a instance se stejnými typy, použijte stejný typ zásad

V následujícím příkladu `Dictionary<int,int>` je zásada přiřazena pouze v `Browse` případě, že má modul jiný důvod k tomu, aby ji bylo možné udělit `Browse` zásadám (což by jinak představovalo výchozí chování); všechny ostatní instance <xref:System.Collections.Generic.Dictionary%602> budou mít všechny členy, které budou procházet.

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

### <a name="how-policy-is-inferred"></a>Způsob odvození zásad

Každý typ zásad má jinou sadu pravidel, která určují, jak bude mít přítomnost tohoto typu zásad vliv na jiné konstrukce.

#### <a name="the-effect-of-browse-policy"></a>Účinek zásad procházení

Použití `Browse` zásad na typ zahrnuje následující změny zásad:

- Základní typ tohoto typu je označený `Browse` zásadou.

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena `Browse` zásadou.

- Pokud je typ delegát, `Invoke` metoda na typu je označena `Dynamic` zásadou.

- Každé rozhraní typu je označeno `Browse` zásadou.

- Typ každého atributu použitého pro typ je označený `Browse` zásadou.

- Pokud je typ obecný, je každý typ omezení označený `Browse` zásadou.

- Pokud je typ obecný, typy, přes které je vytvořen typ, jsou označeny `Browse` zásadou.

Použití `Browse` zásad na metodu zahrnuje následující změny zásad:

- Každý typ parametru metody je označený `Browse` zásadou.

- Návratový typ metody je označený `Browse` zásadou.

- Nadřazený typ metody je označený `Browse` zásadou.

- Pokud je metoda instancí generické metody, je obecná metoda uninstance označena `Browse` zásadou.

- Typ každého atributu, který je použit pro metodu, je označen `Browse` zásadou.

- Pokud je metoda obecná, je každý typ omezení označený `Browse` zásadou.

- Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny `Browse` zásadou.

Použití `Browse` zásad u pole zahrnuje následující změny zásad:

- Typ každého atributu, který je použit pro pole, je označen `Browse` zásadami.

- Typ pole je označený `Browse` zásadou.

- Typ, ke kterému pole patří, je označen `Browse` zásadou.

#### <a name="the-effect-of-dynamic-policy"></a>Účinek dynamických zásad

Použití `Dynamic` zásad na typ zahrnuje následující změny zásad:

- Základní typ tohoto typu je označený `Dynamic` zásadou.

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena `Dynamic` zásadou.

- Pokud typ je typ delegáta, `Invoke` metoda na typu je označena `Dynamic` zásadou.

- Každé rozhraní typu je označeno `Browse` zásadou.

- Typ každého atributu použitého pro typ je označený `Browse` zásadou.

- Pokud je typ obecný, je každý typ omezení označený `Browse` zásadou.

- Pokud je typ obecný, typy, přes které je vytvořen typ, jsou označeny `Browse` zásadou.

Použití `Dynamic` zásad na metodu zahrnuje následující změny zásad:

- Každý typ parametru metody je označený `Browse` zásadou.

- Návratový typ metody je označený `Dynamic` zásadou.

- Nadřazený typ metody je označený `Dynamic` zásadou.

- Pokud je metoda instancí generické metody, je obecná metoda uninstance označena `Browse` zásadou.

- Typ každého atributu, který je použit pro metodu, je označen `Browse` zásadou.

- Pokud je metoda obecná, je každý typ omezení označený `Browse` zásadou.

- Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny `Browse` zásadou.

- Metodu lze vyvolat pomocí `MethodInfo.Invoke` a vytvoření delegáta bude možné provést pomocí <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType> .

Použití `Dynamic` zásad u pole zahrnuje následující změny zásad:

- Typ každého atributu, který je použit pro pole, je označen `Browse` zásadami.

- Typ pole je označený `Dynamic` zásadou.

- Typ, ke kterému pole patří, je označen `Dynamic` zásadou.

#### <a name="the-effect-of-activation-policy"></a>Účinek zásad aktivace

Použití zásad aktivace u typu zahrnuje následující změny zásad:

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena `Browse` zásadou.

- Pokud typ je typ delegáta, `Invoke` metoda na typu je označena `Dynamic` zásadou.

- Konstruktory typu jsou označeny `Activation` zásadou.

Použití `Activation` zásad na metodu zahrnuje následující změnu zásad:

- Konstruktor může být vyvolán <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> metodami a. Pro metody `Activation` má zásada vliv pouze na konstruktory.

Použití `Activation` zásad na pole nemá žádný vliv.

#### <a name="the-effect-of-serialize-policy"></a>Účinek zásad serializace

`Serialize`Zásady umožňují použití běžných serializátorů založených na reflexi. Vzhledem k tomu, že společnost Microsoft nezná přesné vzory přístupu k reflexi serializátorů od jiných společností než Microsoftu, tato zásada nemusí být zcela účinná.

Použití `Serialize` zásad na typ zahrnuje následující změny zásad:

- Základní typ tohoto typu je označený `Serialize` zásadou.

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena `Browse` zásadou.

- Pokud typ je typ delegáta, `Invoke` metoda na typu je označena `Dynamic` zásadou.

- Pokud je typ výčet, pole typu je označeno `Serialize` zásadou.

- Pokud typ implementuje <xref:System.Collections.Generic.IEnumerable%601> , `T` je označen `Serialize` zásadou.

- Pokud je typ <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.Generic.IList%601> ,, <xref:System.Collections.Generic.ICollection%601> <xref:System.Collections.Generic.IReadOnlyCollection%601> , nebo <xref:System.Collections.Generic.IReadOnlyList%601> , pak `T[]` a <xref:System.Collections.Generic.List%601> označený `Serialize` zásadou., ale žádné členy typu rozhraní nejsou označeny `Serialize` zásadou.

- Pokud je typ <xref:System.Collections.Generic.List%601> , žádné členy typu nejsou označeny `Serialize` zásadou.

- Pokud je typ <xref:System.Collections.Generic.IDictionary%602> , <xref:System.Collections.Generic.Dictionary%602> je označen `Serialize` zásadou. ale žádné členy typu nejsou označeny `Serialize` zásadou.

- Pokud je typ <xref:System.Collections.Generic.Dictionary%602> , žádné členy typu nejsou označeny `Serialize` zásadou.

- Pokud typ implementuje <xref:System.Collections.Generic.IDictionary%602> `TKey` a `TValue` jsou označeny `Serialize` zásadou.

- Každý konstruktor, každý přistupující objekt vlastnosti a každé pole je označeno `Serialize` zásadou.

Použití `Serialize` zásad na metodu zahrnuje následující změny zásad:

- Nadřazený typ je označený `Serialize` zásadou.

- Návratový typ metody je označený `Serialize` zásadou.

Použití `Serialize` zásad u pole zahrnuje následující změny zásad:

- Nadřazený typ je označený `Serialize` zásadou.

- Typ pole je označený `Serialize` zásadou.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>Vliv zásad XmlSerializer, DataContractSerializer a DataContractJsonSerializer

Na rozdíl od `Serialize` zásady, která je určena pro serializátory založené na reflexi <xref:System.Xml.Serialization.XmlSerializer> , <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jsou použity zásady, a pro povolení sady serializátorů, které jsou známy .NET Nativemu řetězu nástrojů. Tyto serializátory nejsou implementovány pomocí reflexe, ale sada typů, které lze serializovat za běhu, je určena podobným způsobem jako typy, které jsou reflektované.

Použití jedné z těchto zásad na typ umožňuje serializovat typ pomocí odpovídajícího serializátoru. Všechny typy, které může modul serializace staticky určit jako nutnost serializace, budou také serializovatelný.

Tyto zásady nemají žádný vliv na metody nebo pole.

Další informace najdete v části "rozdíly v Serializacích" v tématu [migrace aplikace pro Windows Store na .NET Native](migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Viz také

- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Reflexe a .NET Native](reflection-and-net-native.md)
