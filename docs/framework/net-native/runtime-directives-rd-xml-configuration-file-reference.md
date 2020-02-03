---
title: Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)
ms.date: 03/30/2017
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
ms.openlocfilehash: e74d34693446cca645003a9f93bc1777849e3182
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
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

Element [knihovny](library-element-net-native.md) má jeden atribut `Name`, který určuje název knihovny nebo sestavení bez přípony souboru. Například následující prvek [knihovny](library-element-net-native.md) se vztahuje na sestavení s názvem Extensions. dll.

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

Samotný prvek [aplikace](application-element-net-native.md) a podřízené prvky [knihovny](library-element-net-native.md) a prvků [aplikace](application-element-net-native.md) expresní zásady; To znamená, že definují způsob, jakým může aplikace použít reflexi u prvku programu. Typ zásady je definován atributem elementu (například `Serialize`). Hodnota zásady je definována hodnotou atributu (například `Serialize="Required"`).

Všechny zásady určené atributem elementu se vztahují na všechny podřízené prvky, které neurčují hodnotu pro tuto zásadu. Například pokud je zásada určena prvkem [typu](type-element-net-native.md) , tato zásada platí pro všechny obsažené typy a členy, pro které není explicitně určena zásada.

Zásady, které může vyjádřit [aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) , se liší od zásad, které je možné vyjádřit pro jednotlivé členy ( [metodou](method-element-net-native.md), [vlastností](property-element-net-native.md), [polem](field-element-net-native.md)a [událostmi](event-element-net-native.md) ).

### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Určení zásad pro sestavení, obory názvů a typy

[Aplikace](application-element-net-native.md), [sestavení](assembly-element-net-native.md), [AttributeImplies](attributeimplies-element-net-native.md), [obor názvů](namespace-element-net-native.md), [podtypy](subtypes-element-net-native.md)a elementy [typu](type-element-net-native.md) podporují následující typy zásad:

- `Activate`. Řídí přístup k konstruktorům za běhu, aby bylo možné povolit aktivaci instancí.

- `Browse`. Řídí dotazování pro informace o prvcích programu, ale neumožňuje přístup k modulu runtime.

- `Dynamic`. Řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování.

- `Serialize`. Řídí přístup za běhu k konstruktorům, polím a vlastnostem, aby bylo možné instance typu serializovat a serializovat pomocí knihoven třetích stran, jako je například serializátor Newtonsoft JSON.

- `DataContractSerializer`. Řídí zásady pro serializaci, která používá třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.

- `DataContractJsonSerializer`. Řídí zásady pro serializaci JSON, které používají třídu <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.

- `XmlSerializer`. Řídí zásady pro serializaci XML, které používají třídu <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>.

- `MarshalObject`. Řídí zásady pro zařazování typů odkazů do WinRT a COM.

- `MarshalDelegate`. Řídí zásady pro zařazování typů delegátů jako ukazatelů funkcí do nativního kódu.

- `MarshalStructure`. Řídí zásady pro zařazování struktur do nativního kódu.

Nastavení přidružená k těmto typům zásad jsou:

- `All`. Povolte zásadu pro všechny typy a členy, které řetěz nástroje neodebere.

- `Auto`. Použijte výchozí chování. (Není-li určena zásada, je ekvivalentní nastavení této zásady na `Auto`, pokud tato zásada není přepsána, například nadřazeným prvkem.)

- `Excluded`. Zakáže zásady pro prvek programu.

- `Public`. Povolte zásadu pro veřejné typy nebo členy, pokud řetěz nástrojů nezjistí, že je člen zbytečný a proto jej odebere. (V druhém případě je nutné použít `Required Public` k zajištění toho, že člen je udržován a má možnosti reflexe.)

- `PublicAndInternal`. Povolte zásady pro veřejné a interní typy nebo členy, pokud je řetěz nástrojů neodebere.

- `Required Public`. Vyžaduje, aby řetěz nástrojů zachoval veřejné typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.

- `Required PublicAndInternal`. Vyžaduje, aby řetěz nástrojů zachoval veřejné i interní typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.

- `Required All`. Vyžaduje, aby řetězec nástroje zachoval všechny typy a členy bez ohledu na to, jestli se používají, a povolil pro ně zásady.

Například následující direktivy modulu runtime definují zásadu pro všechny typy a členy v souboru DataClasses. dll sestavení. Umožňuje reflexi pro serializaci všech veřejných vlastností, umožňuje procházení pro všechny typy a členy typu, umožňuje aktivaci pro všechny typy (z důvodu `Dynamic` atributu) a povoluje reflexi pro všechny veřejné typy a členy.

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

- `Browse` – řídí dotazování pro informace o tomto členu, ale nepovoluje přístup za běhu.

- `Dynamic` – řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování. Také ovládá dotazování na informace o nadřazeného typu.

- `Serialize` – řídí přístup k členu za běhu, aby se mohly instance typů serializovat a deserializovat pomocí knihoven, jako je Newtonsoft JSON serializátor. Tuto zásadu lze použít na konstruktory, pole a vlastnosti.

[Metoda](method-element-net-native.md) a prvky [události](event-element-net-native.md) podporují následující typy zásad:

- `Browse` – řídí dotazování pro informace o tomto členu, ale nepovoluje přístup za běhu.

- `Dynamic` – řídí přístup za běhu ke všem členům typu, včetně konstruktorů, metod, polí, vlastností a událostí, pro povolení dynamického programování. Také ovládá dotazování na informace o nadřazeného typu.

 Nastavení přidružená k těmto typům zásad jsou:

- `Auto` – použije výchozí chování. (Pokud se nezadá zásada, bude se jednat o nastavení této zásady, aby se `Auto`, pokud je něco nepřepisuje.)

- `Excluded` – nikdy Nezahrnovat metadata pro člena.

- `Included` – povolí zásadu, pokud se ve výstupu nachází nadřazený typ.

- `Required` – vyžaduje, aby řetěz nástrojů zachoval tento člen, i když se zdá být nepoužitý, a pro něj povolí zásady.

## <a name="runtime-directives-file-semantics"></a>Sémantika souboru direktiv modulu runtime

Zásady lze definovat současně pro elementy vyšší úrovně i na nižší úrovni. Například zásada může být definována pro sestavení a pro některé typy obsažené v tomto sestavení. Pokud není určitý element na nižší úrovni reprezentován, zdědí zásady jeho nadřazeného objektu. Například pokud `Assembly` element je přítomen, ale `Type` prvky nejsou, zásada zadaná v prvku `Assembly` se vztahuje na každý typ v sestavení. U stejného prvku programu lze také použít více prvků. Například samostatné prvky [sestavení](assembly-element-net-native.md) mohou definovat stejný prvek zásad pro stejné sestavení odlišně. V následujících částech se dozvíte, jak se v těchto případech vyřeší zásada pro konkrétní typ.

[Typ](type-element-net-native.md) nebo prvek [metody](method-element-net-native.md) obecného typu nebo metody aplikuje zásady na všechny instance, které nemají vlastní zásady. Například element `Type`, který určuje zásadu pro <xref:System.Collections.Generic.List%601>, se vztahuje na všechny vytvořené instance tohoto obecného typu, pokud není přepsán pro konkrétní konstruovaný typ (například `List<Int32>`) pomocí elementu `TypeInstantiation`. V opačném případě elementy definují zásady pro prvek program s názvem.

Pokud je prvek dvojznačný, modul hledá shody a pokud najde přesnou shodu, bude ho používat. Pokud najde více shod, dojde k upozornění nebo chybě.

### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>Pokud dvě direktivy používají zásady na stejný prvek programu

Pokud se dva prvky v různých souborech běhových direktiv pokusí nastavit stejný typ zásad pro stejný prvek programu (například sestavení nebo typ) na jiné hodnoty, konflikt je vyřešen následujícím způsobem:

1. Pokud `Excluded` element je přítomen, má přednost.

2. `Required` má přednost před ne`Required`m.

3. `All` má přednost před `PublicAndInternal`, která má přednost před `Public`.

4. Jakékoli explicitní nastavení má přednost před `Auto`.

Například pokud jeden projekt obsahuje následující dva soubory běhových direktiv, zásada serializace pro DataClasses. dll je nastavena na `Required Public` i `All`. V takovém případě by zásada serializace byla vyřešena jako `Required All`.

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

Podřízené prvky přepíšou své nadřazené prvky, včetně nastavení `Excluded`. Přepsání je hlavní důvod, proč byste chtěli zadat `Auto`.

V následujícím příkladu je nastavení zásad serializace pro vše v `DataClasses`, které není v `DataClasses.ViewModels`, `Required Public`a vše, co je v `DataClasses` i `DataClasses.ViewModels`, by `All`.

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

V následujícím příkladu je `Dictionary<int,int>` přiřazena zásada `Browse` pouze v případě, že má motor jiný důvod k tomu, aby se mu přidělila zásada `Browse` (která by jinak představovala výchozí chování); všechny ostatní instance <xref:System.Collections.Generic.Dictionary%602> budou procházet všechny jeho členy.

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

Použití zásad `Browse` na typ zahrnuje následující změny zásad:

- Základní typ tohoto typu je označený zásadou `Browse`.

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.

- Pokud je typ delegát, je metoda `Invoke` v typu označena zásadou `Dynamic`.

- Každé rozhraní typu je označeno zásadou `Browse`.

- Typ každého atributu, který je použit pro typ, je označen zásadou `Browse`.

- Pokud je typ obecný, je každý typ omezení označený zásadou `Browse`.

- Pokud je typ obecný, typy, jejichž instance jsou vytvořeny, jsou označeny zásadou `Browse`.

Použití zásad `Browse` pro metodu zahrnuje následující změny zásad:

- Každý typ parametru metody je označený zásadou `Browse`.

- Návratový typ metody je označený zásadou `Browse`.

- Nadřazený typ metody je označený zásadou `Browse`.

- Pokud je metoda instancí generické metody, je obecná metoda uninstance označena zásadou `Browse`.

- Typ každého atributu, který je použit pro metodu, je označen zásadou `Browse`.

- Pokud je metoda obecná, každý typ omezení je označený zásadou `Browse`.

- Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny zásadou `Browse`.

Použití zásad `Browse` u pole zahrnuje tyto změny zásad:

- Typ každého atributu, který se používá pro pole, je označený zásadou `Browse`.

- Typ pole je označený zásadou `Browse`.

- Typ, ke kterému pole patří, je označen zásadou `Browse`.

#### <a name="the-effect-of-dynamic-policy"></a>Účinek dynamických zásad

Použití zásad `Dynamic` na typ zahrnuje následující změny zásad:

- Základní typ tohoto typu je označený zásadou `Dynamic`.

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Dynamic`.

- Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.

- Každé rozhraní typu je označeno zásadou `Browse`.

- Typ každého atributu, který je použit pro typ, je označen zásadou `Browse`.

- Pokud je typ obecný, je každý typ omezení označený zásadou `Browse`.

- Pokud je typ obecný, typy, jejichž instance jsou vytvořeny, jsou označeny zásadou `Browse`.

Použití zásad `Dynamic` pro metodu zahrnuje následující změny zásad:

- Každý typ parametru metody je označený zásadou `Browse`.

- Návratový typ metody je označený zásadou `Dynamic`.

- Nadřazený typ metody je označený zásadou `Dynamic`.

- Pokud je metoda instancí generické metody, je obecná metoda uninstance označena zásadou `Browse`.

- Typ každého atributu, který je použit pro metodu, je označen zásadou `Browse`.

- Pokud je metoda obecná, každý typ omezení je označený zásadou `Browse`.

- Pokud je metoda obecná, typy, přes které je vytvořena instance metody, jsou označeny zásadou `Browse`.

- Metodu lze vyvolat pomocí `MethodInfo.Invoke`a je možné vytvořit delegáta pomocí <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.

Použití zásad `Dynamic` u pole zahrnuje tyto změny zásad:

- Typ každého atributu, který se používá pro pole, je označený zásadou `Browse`.

- Typ pole je označený zásadou `Dynamic`.

- Typ, ke kterému pole patří, je označen zásadou `Dynamic`.

#### <a name="the-effect-of-activation-policy"></a>Účinek zásad aktivace

Použití zásad aktivace u typu zahrnuje následující změny zásad:

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.

- Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.

- Konstruktory typu jsou označené zásadou `Activation`.

Použití zásad `Activation` pro metodu zahrnuje následující změnu zásad:

- Konstruktor může být vyvolán metodami <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> a <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>. Pro metody má zásada `Activation` vliv pouze na konstruktory.

Použití zásad `Activation` pro pole nemá žádný vliv.

#### <a name="the-effect-of-serialize-policy"></a>Účinek zásad serializace

Zásady `Serialize` umožňují použití běžných serializátorů založených na reflexi. Vzhledem k tomu, že společnost Microsoft nezná přesné vzory přístupu k reflexi serializátorů od jiných společností než Microsoftu, tato zásada nemusí být zcela účinná.

Použití zásad `Serialize` na typ zahrnuje následující změny zásad:

- Základní typ tohoto typu je označený zásadou `Serialize`.

- Pokud se jedná o instanci generického typu, je nevytvořená verze typu označena zásadou `Browse`.

- Pokud typ je typ delegáta, metoda `Invoke` v typu je označená pomocí zásad `Dynamic`.

- Pokud je typ výčet, pole typu je označeno zásadou `Serialize`.

- Pokud typ implementuje <xref:System.Collections.Generic.IEnumerable%601>, `T` je označen zásadou `Serialize`.

- Pokud je typ <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>nebo <xref:System.Collections.Generic.IReadOnlyList%601>, pak `T[]` a <xref:System.Collections.Generic.List%601> označené zásadou pro `Serialize`. nejsou ale žádné členy typu rozhraní označené zásadami pro `Serialize`.

- Pokud je typ <xref:System.Collections.Generic.List%601>, žádné členy typu nejsou označeny zásadami `Serialize`.

- Pokud je typ <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> je označený zásadou `Serialize`. ale žádní členové typu nejsou označeni pomocí zásad `Serialize`.

- Pokud je typ <xref:System.Collections.Generic.Dictionary%602>, žádné členy typu nejsou označeny zásadami `Serialize`.

- Pokud typ implementuje <xref:System.Collections.Generic.IDictionary%602>, `TKey` a `TValue` jsou označeny zásadami `Serialize`.

- Každý konstruktor, každý přistupující objekt vlastnosti a každé pole je označeno zásadou `Serialize`.

Použití zásad `Serialize` pro metodu zahrnuje následující změny zásad:

- Nadřazený typ je označený zásadou `Serialize`.

- Návratový typ metody je označený zásadou `Serialize`.

Použití zásad `Serialize` u pole zahrnuje tyto změny zásad:

- Nadřazený typ je označený zásadou `Serialize`.

- Typ pole je označený zásadou `Serialize`.

#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserializer-policies"></a>Vliv zásad XmlSerializer, DataContractSerializer a DataContractJsonSerializer

Na rozdíl od `Serialize` zásady, která je určena pro serializátory založené na reflexi, jsou použity zásady <xref:System.Xml.Serialization.XmlSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer>a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k povolení sady serializátorů, které jsou známé jako řetězec nástroje .NET Native. Tyto serializátory nejsou implementovány pomocí reflexe, ale sada typů, které lze serializovat za běhu, je určena podobným způsobem jako typy, které jsou reflektované.

Použití jedné z těchto zásad na typ umožňuje serializovat typ pomocí odpovídajícího serializátoru. Všechny typy, které může modul serializace staticky určit jako nutnost serializace, budou také serializovatelný.

Tyto zásady nemají žádný vliv na metody nebo pole.

Další informace najdete v části "rozdíly v Serializacích" v tématu [migrace aplikace pro Windows Store na .NET Native](migrating-your-windows-store-app-to-net-native.md).

## <a name="see-also"></a>Viz také

- [Elementy direktivy modulu runtime](runtime-directive-elements.md)
- [Reflexe a .NET Native](reflection-and-net-native.md)
