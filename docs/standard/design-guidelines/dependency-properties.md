---
title: Vlastnosti závislosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: 476ef1bb1ac5ec1f551979c64a41cbae55c554bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280254"
---
# <a name="dependency-properties"></a>Vlastnosti závislosti
Vlastnost závislosti (DP) je obvyklá vlastnost, která ukládá její hodnotu do úložiště vlastností místo jejich uložení do proměnné typu (pole), například.

 Připojená vlastnost Dependency je druh vlastnosti závislosti, která se modeluje jako statické metody Get a set, které představují vlastnosti popisující vztahy mezi objekty a jejich kontejnery (například umístění `Button` objektu na `Panel` kontejneru).

 ✔️ Zadejte vlastnosti závislosti, pokud potřebujete vlastnosti pro podporu funkcí WPF, jako jsou například styly, triggery, datové vazby, animace, dynamické prostředky a dědičnost.

## <a name="dependency-property-design"></a>Návrh vlastnosti závislosti
 <xref:System.Windows.DependencyObject>při implementaci vlastností závislosti ✔️ dědit z nebo jeden z jeho podtypů. Typ poskytuje velmi efektivní implementaci úložiště vlastností a automaticky podporuje datovou vazbu WPF.

 ✔️ poskytují regulární vlastnost CLR a veřejné statické pole jen pro čtení, které ukládá instanci <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> pro každou vlastnost závislosti.

 ✔️ implementovat vlastnosti závislosti voláním metod instance <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> a <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> .

 ✔️ Pojmenujte statické pole vlastnosti závislosti příponou názvu vlastnosti s vlastností.

 ❌Nenastavte výchozí hodnoty vlastností závislosti explicitně v kódu; místo toho je nastavte v metadatech.

 Pokud nastavíte výchozí nastavení vlastnosti explicitně, můžete zabránit tomu, aby se tato vlastnost nastavila některými implicitními prostředky, jako je styl.

 ❌Neumísťujte kód do jiných přístupových objektů vlastností než standardní kód pro přístup k statickému poli.

 Tento kód nebude proveden, pokud je vlastnost nastavena pomocí implicitních prostředků, jako je například styl, protože styl používá přímo pole static.

 ❌Nepoužívejte vlastnosti závislosti k ukládání zabezpečených dat. K vlastnostem soukromé závislosti lze přistupovat i na veřejném.

## <a name="attached-dependency-property-design"></a>Návrh vlastnosti připojené závislosti
 Vlastnosti závislosti popsané v předchozí části označují vnitřní vlastnosti deklarovaného typu; `Text`vlastnost je například vlastnost `TextButton` , která ji deklaruje. Speciálním druhem vlastnosti závislosti je vlastnost připojené závislosti.

 Klasickým příkladem připojené vlastnosti je <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> vlastnost. Vlastnost představuje pozici sloupce tlačítko (ne mřížka), ale je relevantní pouze v případě, že je tlačítko obsaženo v mřížce, a proto je "připojené" k tlačítkům na základě mřížky.

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 Definice připojené vlastnosti vypadá hlavně podobně jako vlastnost běžné závislosti s tím rozdílem, že přistupující objekty jsou reprezentovány pomocí statických metod get a set:

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a>Ověřování vlastností závislosti
 Vlastnosti často implementují, co se nazývá ověřování. Logika ověřování se spustí, když se provede pokus o změnu hodnoty vlastnosti.

 Přístupové objekty vlastnosti bohužel nemůžou obsahovat libovolný ověřovací kód. Místo toho je nutné při registraci vlastnosti zadat logiku ověřování vlastností závislostí.

 ❌Do přístupových objektů vlastnosti neumísťujte logiku ověřování vlastností závislostí. Místo toho předejte metodu zpětného volání ověření do `DependencyProperty.Register` metody.

## <a name="dependency-property-change-notifications"></a>Oznámení o změně vlastnosti závislosti
 ❌Neimplementujte logiku oznámení změn v přístupových parametrech vlastnosti závislosti. Vlastnosti závislosti mají vestavěnou funkci oznámení změn, kterou je nutné použít při poskytnutí zpětného volání oznámení o změně do <xref:System.Windows.PropertyMetadata> .

## <a name="dependency-property-value-coercion"></a>Hodnota vlastnosti závislosti – vynucení
 K převodu vlastnosti dojde, pokud je hodnota zadaná metodě setter vlastnosti změněna před samotným úpravou úložiště vlastností.

 ❌Neimplementujte logiku vynucení v přístupových parametrech vlastnosti závislosti.

 Vlastnosti závislosti mají integrovanou funkci pro vynucení a lze ji použít poskytnutím zpětného volání do `PropertyMetadata` .

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Běžné vzory návrhu](common-design-patterns.md)
