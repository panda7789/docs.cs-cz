---
title: Kopírování a přichycování
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1696bd6eb4eb3a43593cf7ed264c80745c1ec66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643513"
---
# <a name="copying-and-pinning"></a>Kopírování a přichycování

Při zařazování dat, interoperační zařazovač můžete kopírovat nebo připnout dat se zařadit. Kopírování dat umístí kopii dat z jednoho umístění v paměti do jiného umístění v paměti. Následující obrázek znázorňuje rozdíly mezi kopírování typu hodnoty a kopírování typu předány podle odkazu ze spravované na nespravované paměti.

![Diagram znázorňující, jak jsou zkopírovány hodnoty a referenční typy.](./media/copying-and-pinning/interop-marshal-copy.gif)

Argumenty metody předán podle hodnoty jsou zařazení na nespravovaný kód jako hodnoty v zásobníku. Proces kopírování je s přímým přístupem. Argumenty předány podle odkazu jsou předány jako ukazatele do zásobníku. Typy odkazů jsou také předán podle hodnoty a podle reference. Jak ukazuje následující obrázek, typy odkazů, předán podle hodnoty jsou zkopírovány nebo připnout:

![Diagram znázorňující referenční typy předán podle hodnoty a podle reference.](./media/copying-and-pinning/interop-marshal-reference-pin.gif)

Připnutí dočasně uzamkne dat v aktuálním umístění paměti, tak jeho synchronizaci z právě přemístění uvolňováním paměti modulu common language runtime. Aby zařazování odvozovalo připíná data s cílem snížit režijní náklady na kopírování a zvýšit výkon. Typ dat určuje, zda se zkopíroval nebo připnout během procesu zařazování.  Připnutí se provádí automaticky při zařazování pro objekty, jako <xref:System.String>, ale můžete také ručně připnout použití paměti <xref:System.Runtime.InteropServices.GCHandle> třídy.

## <a name="formatted-blittable-classes"></a>Formátovaný Blittable třídy

Ve formátu [blittable](blittable-and-non-blittable-types.md) třídy opravili rozložení (ve formátu) a běžné reprezentace dat v obou spravované a nespravované paměti. Pokud tyto typy vyžadují zařazování, ukazatel na objekt v haldě volaný předána přímo. Volaný může změnit obsah z umístění v paměti se na ně odkazovat ukazatel.

> [!NOTE]
> Volaný můžete změnit obsah paměti, když je parametr označený Out nebo In/Out. Naproti tomu volaný byste se vyhnout změny obsahu, pokud parametr je nastaven k zařazování podle, což je výchozí nastavení pro formátovaný přenositelné typy. Úprava objektu v generuje problémy, když se do knihovny typů exportuje stejné třídy a použít pro volání mezi objektu apartment.

## <a name="formatted-non-blittable-classes"></a>Formátovaný nepřenositelné třídy

Ve formátu [nepřenositelné](blittable-and-non-blittable-types.md) třídy opravili rozložení (ve formátu), ale reprezentace dat se liší ve spravované a nespravované paměti. Data můžou vyžadovat transformace za následujících podmínek:

- Pokud je třída nepřenositelné zařazen podle hodnoty, volaný přijímá ukazatel na kopii struktury dat.

- Pokud třída nepřenositelné je zařazen podle odkazu, volaný přijímá ukazatel na ukazatel na kopii struktury dat.

- Pokud <xref:System.Runtime.InteropServices.InAttribute> atribut je nastaven, tato kopie je vždy inicializovat stavem instance zařazování podle potřeby.

- Pokud <xref:System.Runtime.InteropServices.OutAttribute> atribut je nastaven, stav je vždy zkopírována zpět k instanci na vrátit, zařazování podle potřeby.

- Pokud mají oba **InAttribute** a **OutAttribute** je nastaveno, jsou požadovány obě kopie. Pokud je buď atribut vynechán, aby zařazování odvozovalo můžete optimalizovat odstraněním zkopírujte.

## <a name="reference-types"></a>Typy odkazů

Odkazové typy je možné předat hodnotou nebo odkazem. Když jsou předávány hodnotou, je ukazatel na typ předány do zásobníku. Když jsou předány podle odkazu, je ukazatel na ukazatel na typ předány do zásobníku.

Odkazové typy mají následující podmíněné chování:

- Pokud typ odkazu je předán podle hodnoty a má členy nepřenositelné typy, typy jsou převedeny dvakrát:

  - Když je argument předaný do nespravované oblasti.

  - Při návratu z volání.

  Aby se zabránilo zbytečně kopírování a převod, tyto typy jsou zařazeny jako v parametry. Musíte explicitně použít **InAttribute** a **OutAttribute** atributy na argument pro volajícího, aby se změny provedené volaným.

- Pokud typ odkazu je předán podle hodnoty a obsahuje pouze členy typů blittable, je možné připnout při zařazování a všechny změny provedené členy typu volaným jsou vidět volajícím. Použít **InAttribute** a **OutAttribute** explicitně, pokud chcete toto chování. Bez těchto směrové atributy interoperační zařazovač neexportuje směrové informace do knihovny typů (exportuje jako v, což je výchozí hodnota) a to může způsobit problémy s zařazování mezi apartment modelu COM.

- Pokud typ odkazu je předána odkazem, ji budou zařadit jako vstup a výstup ve výchozím nastavení.

## <a name="systemstring-and-systemtextstringbuilder"></a>System.String a System.Text.StringBuilder

Při dat je zařazení na nespravovaný kód podle hodnoty nebo podle odkazu, aby zařazování odvozovalo obvykle zkopíruje data do sekundární vyrovnávací paměti (pravděpodobně převodu znakové sady během kopírování) a předá volaný odkaz do vyrovnávací paměti. Pokud je odkaz **BSTR** alokována **SysAllocString**, odkaz je vždy přidělena pomocí **CoTaskMemAlloc**.

Jako optimalizace při buď typ řetězce je zařazen podle hodnoty (například řetězce znaků Unicode), aby zařazování odvozovalo předá volaný přímý ukazatel spravované řetězce ve vnitřní vyrovnávací paměti Unicode místo jeho kopírování vyrovnávací paměť nového.

> [!CAUTION]
> Pokud řetězec je předán podle hodnoty, volaný musí nikdy změnit odkaz předávány zařazování. To může dojít k poškození spravované haldě.

Když <xref:System.String?displayProperty=nameWithType> je předána odkazem, aby zařazování odvozovalo zkopíruje obsah řetězce do vyrovnávací paměti, sekundární před uskutečněním hovoru. Potom zkopíruje obsah vyrovnávací paměti do nového řetězce při návratu z volání. Tento postup zajišťuje, zůstane neměnné spravované řetězce beze změny.

Když <xref:System.Text.StringBuilder?displayProperty=nameWithType> je předán podle hodnoty, předá zařazování odkaz na vnitřní vyrovnávací paměť **StringBuilder** přímo k volajícímu. Volajícím a volaným musí shodnout na velikost vyrovnávací paměti. Volající zodpovídá za vytvoření **StringBuilder** odpovídající délky. Volaný musí přijmout nezbytná opatření pro zajištění, že není přetečení vyrovnávací paměti. **StringBuilder** je výjimkou z pravidla, odkazující na typy, předán podle hodnoty jsou předány jako parametry in ve výchozím nastavení. Vždy je předána jako vstup a výstup.

## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Zařazování spolupráce](interop-marshaling.md)
