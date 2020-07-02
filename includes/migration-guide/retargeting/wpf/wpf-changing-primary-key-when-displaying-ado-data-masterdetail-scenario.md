---
ms.openlocfilehash: 35fc4782ebbba33f5fc6668712af9d89d00cafe9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614620"
---
### <a name="wpf-changing-a-primary-key-when-displaying-ado-data-in-a-masterdetail-scenario"></a>WPF měnící primární klíč při zobrazení dat ADO ve scénáři hlavní/podrobnosti

#### <a name="details"></a>Podrobnosti

Předpokládejme, že máte kolekci položek typu ADO `Order` s relací s názvem OrderDetails, která &quot; &quot; ji souvisí s kolekcí položek typu `Detail` prostřednictvím pole ČísloObjednávky primárního klíče &quot; &quot; . V aplikaci WPF můžete vytvořit propojení ovládacího prvku seznam s podrobnostmi o daném pořadí:

```xaml
<ListBox ItemsSource="{Binding Path=OrderDetails}" >
```

kde DataContext je `Order` . WPF Získá hodnotu `OrderDetails` vlastnosti-a kolekci D všech `Detail` položek, jejichž `OrderID` `OrderID` počet odpovídá hlavní položce. Změna chování nastane při změně primárního klíče `OrderID` hlavní položky. ADO automaticky změní `OrderID` všechny ovlivněné záznamy v kolekci podrobností (konkrétně ty zkopírované do kolekce D).  Ale co se stane se D?

- Staré chování: kolekce D je zrušená. Hlavní položka *nevyvolává oznámení* o změně vlastnosti `OrderDetails` . Seznam stále používá kolekci D, která je nyní prázdná.
- Nové chování: kolekce D se nezměnila. Každá z jeho položek vyvolá oznámení o změně `OrderID` Vlastnosti. Seznam stále používá kolekci D a zobrazuje podrobnosti s novým `OrderID` . WPF implementuje nové chování vytvořením kolekce D jiným způsobem: voláním metody ADO <xref:System.Data.DataRowView.CreateChildView(System.Data.DataRelation,System.Boolean)?displayProperty=nameWithType> s `followParent` argumentem nastaveným na `true` .

#### <a name="suggestion"></a>Návrh

Aplikace získá nové chování pomocí následujícího přepínače AppContext.

```xml
<configuration>
  <runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Data.DoNotUseFollowParentWhenBindingToADODataRelation=false"/>
  </runtime>
</configuration>
```

Přepínač nastaví výchozí nastavení `true` (staré chování) pro aplikace, které cílí na rozhraní .NET 4.7.1 nebo níže, a na `false` (nové chování) pro aplikace, které cílí na rozhraní .NET 4.7.2 nebo vyšší.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.7.2       |
| Typ    | Změna cílení |
