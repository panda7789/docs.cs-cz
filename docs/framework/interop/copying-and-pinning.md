---
title: Kopírování a přichycování
ms.date: 03/30/2017
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
ms.openlocfilehash: f6db7d37293015911c1285d39e19bf7542a7ac59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123643"
---
# <a name="copying-and-pinning"></a>Kopírování a přichycování

Při zařazování dat může zařazovací modul spolupráce zkopírovat nebo připnout data, která jsou zařazování. Kopírování dat umístí kopii dat z jednoho umístění v paměti v jiném umístění v paměti. Následující ilustrace znázorňuje rozdíly mezi zkopírováním typu hodnoty a zkopírováním typu předaného odkazem ze spravovaného do nespravované paměti.

![Diagram, který ukazuje, jak se zkopírují typy hodnot a odkazů](./media/copying-and-pinning/interop-marshal-copy.gif)

Argumenty metody předané hodnotou jsou zařazeny do nespravovaného kódu jako hodnoty v zásobníku. Proces kopírování je přímý. Argumenty předané odkazem jsou předány jako ukazatelé na zásobníku. Odkazové typy jsou také předávány hodnotou a odkazem. Jak ukazuje následující obrázek, typy odkazů předané hodnotou jsou buď zkopírovány nebo připnuté:

![Diagram znázorňující typy odkazů předané hodnotou a odkazem.](./media/copying-and-pinning/interop-marshal-reference-pin.gif)

Připnutí dočasně uzamkne data v jejich aktuálním umístění v paměti, takže tím brání jejich přemístění systémem uvolňování paměti společného jazykového modulu runtime. Data zařazovacího modulu připnete k omezení režijních nákladů na kopírování a zvýšení výkonu. Typ dat určuje, zda je zkopírován nebo připnuté během procesu zařazování.  Připnutí se provádí automaticky během zařazování pro objekty, jako je <xref:System.String>, ale můžete také ručně připnout paměť pomocí <xref:System.Runtime.InteropServices.GCHandle> třídy.

## <a name="formatted-blittable-classes"></a>Formátované přenositelné třídy

Naformátované [přenositelné třídy mají](blittable-and-non-blittable-types.md) v spravované i nespravované paměti pevné rozložení (naformátované) a běžné reprezentace dat. Pokud tyto typy vyžadují zařazování, ukazatel na objekt v haldě je předán volanému přímo. Volaný může změnit obsah umístění v paměti, na které odkazuje ukazatel.

> [!NOTE]
> Volaný může změnit obsah paměti, pokud je parametr označený jako out nebo out. Naproti tomu by volaný neměl měnit obsah, pokud je parametr nastaven na zařazování jako v, což je výchozí hodnota pro formátované přenositelné typy. Změna v objektu generuje problémy, pokud je stejná třída exportována do knihovny typů a použita k provedení volání křížového typu.

## <a name="formatted-non-blittable-classes"></a>Naformátované třídy, které nejsou přenositelné

Formátované nepřenositelné třídy mají pevně dané rozložení ( [naformátované](blittable-and-non-blittable-types.md) ), ale reprezentace dat se liší ve spravované a nespravované paměti. Data mohou vyžadovat transformaci za následujících podmínek:

- Pokud je třída, která není přenositelná, zařazena podle hodnoty, Volaný obdrží ukazatel na kopii struktury dat.

- Pokud je nepřenosná třída zařazená odkazem, Volaný obdrží ukazatel na ukazatel na kopii struktury dat.

- Pokud je nastaven atribut <xref:System.Runtime.InteropServices.InAttribute>, je tato kopie vždy inicializována se stavem instance, zařazování podle potřeby.

- Pokud je nastaven atribut <xref:System.Runtime.InteropServices.OutAttribute>, stav je vždy zkopírován zpět do instance při návratu, zařazování podle potřeby.

- Pokud jsou nastaveny atributy **InAttribute** i **subattribute** , jsou požadovány obě kopie. Pokud je atribut vynechán, zařazovací modul může být optimalizován vyřazením buď zkopírování.

## <a name="reference-types"></a>Typy odkazů

Odkazové typy mohou být předány hodnotou nebo odkazem. Když jsou předávány hodnotou, ukazatel na typ je předán do zásobníku. Při předání odkazem je ukazatel na ukazatel na typ předán do zásobníku.

Typy odkazů mají následující podmíněné chování:

- Pokud je odkazový typ předán podle hodnoty a má členy nepřenositelného typu, jsou typy převedeny dvakrát:

  - Při předání argumentu nespravované straně.

  - Při návratu z volání.

  Aby nedocházelo k zbytečnému kopírování a převodu, jsou tyto typy zařazeny jako v parametrech. Chcete-li zobrazit změny provedené volaným, je nutné explicitně použít atributy **InAttribute** a Attribute **atributu** na argument volajícího.

- Pokud je odkazový typ předán podle hodnoty a má pouze členy typů, lze jej připnout během zařazování a jakékoli změny provedené u členů typu volanými jsou viditelné volajícím. Pokud chcete toto chování, použijte **atribut InAttribute** a **InAttribute** . Bez těchto směrových atributů nezařazovací modul Interop neexportuje směrující informace do knihovny typů (exportuje se jako v, což je výchozí nastavení), což může způsobit problémy s zařazováním do více platforem modelu COM.

- Pokud typ odkazu přechází odkazem, bude ve výchozím nastavení zařazen jako ve výchozím stavu.

## <a name="systemstring-and-systemtextstringbuilder"></a>System. String a System. text. StringBuilder

Když jsou data zařazena do nespravovaného kódu pomocí hodnoty nebo odkazem, zařazovací objekt obvykle kopíruje data do sekundární vyrovnávací paměti (případně převádějí znakové sady během kopírování) a předá odkaz na vyrovnávací paměť volanému. Pokud odkaz není typu **BSTR** přidělený pomocí **případě**, je odkaz vždy přidělen pomocí **CoTaskMemAlloc**.

Jako optimalizace, pokud je typ řetězce zařazen podle hodnoty (například řetězce znaků Unicode), zařazovací modul před kopírováním do nové vyrovnávací paměti předává volaný přímý ukazatel na spravované řetězce v interní vyrovnávací paměti Unicode.

> [!CAUTION]
> Když je řetězec předán podle hodnoty, volaný nesmí nikdy změnit odkaz předaný zařazovacím objektem. V takovém případě může být poškozena spravovaná halda.

Pokud je předána <xref:System.String?displayProperty=nameWithType> odkazem, zařazovací služba zkopíruje obsah řetězce do sekundární vyrovnávací paměti před provedením volání. Pak zkopíruje obsah vyrovnávací paměti do nového řetězce při návratu z volání. Tato technika zajišťuje, že neměnné spravované řetězce zůstávají beze změny.

Když je <xref:System.Text.StringBuilder?displayProperty=nameWithType> předána hodnotou, zařazovací modul předává odkaz na vnitřní vyrovnávací paměť **StringBuilder** přímo volajícímu. Volající a volaný musí souhlasit s velikostí vyrovnávací paměti. Volající je zodpovědný za vytvoření **StringBuilder** s adekvátní délkou. Volaný musí podniknout nezbytná opatření, aby se zajistilo, že vyrovnávací paměť nebude přetečení. **StringBuilder** je výjimka pro pravidlo, které odkazuje na typy předané hodnotou, ve výchozím nastavení předány jako parametry v parametrech. Vždycky se předává jako vstupně-výstupní.

## <a name="see-also"></a>Viz také:

- [Výchozí chování zařazování](default-marshaling-behavior.md)
- [Směrové atributy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Zařazování spolupráce](interop-marshaling.md)
