---
title: Kopírování a přichycování
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- pinning, interop marshaling
- copying, interop marshaling
- interop marshaling, copying
- interop marshaling, pinning
ms.assetid: 0059f576-e460-4e70-b257-668870e420b8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c785c7bc9160cb252aad61fea00cce0d9a7eacdf
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="copying-and-pinning"></a>Kopírování a přichycování
Při zařazování dat, spolupráce vláken můžete zkopírovat nebo kód pin se zařazené data. Kopírování dat umístí kopii dat z jednoho umístění paměti v jiném umístění paměti. Následující obrázek znázorňuje rozdíly mezi kopírování typ hodnoty a kopírování typu předaná odkaz ze spravované na nespravované paměti.  
  
 ![Hodnota předaná podle hodnoty a podle reference typy](./media/interopmarshalcopy.gif "interopmarshalcopy")  
Typy hodnot předán podle hodnoty a podle reference  
  
 Metoda argumenty předaná hodnota přeuspořádány na nespravovaný kód jako hodnoty v zásobníku. Proces kopírování je SMB direct. Argumenty předávané odkazem jsou předány jako ukazatele v zásobníku. Odkazové typy jsou předávány také podle hodnoty a podle reference. Jak ukazuje následující obrázek, předaná hodnota odkazové typy jsou zkopírovány nebo připnutý.  
  
 ![Zprostředkovatel komunikace s objekty COM](./media/interopmarshalpin.gif "interopmarshalpin")  
Odkazové typy předán podle hodnoty a podle reference  
  
 Připnutí dočasně zamkne dat v aktuálním umístění paměti, proto je zachování z se přemístění podle common language runtime systém uvolňování paměti. Zařazování PIN kódy dat snížit režii kopírování a vylepšují výkon. Typ dat určuje, zda je zkopírovat nebo připnuté během procesu zařazování.  Připnutí se provádí automaticky při zařazování pro objekty, jako <xref:System.String>, ale můžete také ručně připnout paměti pomocí <xref:System.Runtime.InteropServices.GCHandle> třídy.  
  
## <a name="formatted-blittable-classes"></a>Formátovaný přenositelné třídy  
 Formátovaný [přenositelné](blittable-and-non-blittable-types.md) třídy opravili rozložení (ve formátu) a běžné reprezentace dat v obou spravovaných a nespravovaných paměti. Pokud tyto typy vyžadují kódování, ukazatel na objekt v haldě je předán volaného přímo. Volaného můžete změnit obsah umístění v paměti se na ně odkazovat ukazatele.  
  
> [!NOTE]
>  Obsah paměti můžete změnit volaného, pokud parametr je označen jako Out či vstup/výstup. Naproti tomu volaného byste neměli Změna obsahu, pokud parametr je nastaven na zařazování jako v což je výchozí nastavení pro formátovaný přenositelné typy. Úprava objektu v generuje problémy, když se stejnou třídu exportují do knihovny typů a použít k volání mezi apartment.  
  
## <a name="formatted-non-blittable-classes"></a>Formátovaný nepřenositelné třídy  
 Formátovaný [nepřenositelné](blittable-and-non-blittable-types.md) třídy opravili rozložení (ve formátu), ale reprezentace dat se liší v spravovanými a nespravovanými paměti. Data můžete vyžadovat transformace za následujících podmínek:  
  
-   Pokud je třída nepřenositelné zařazena pomocí hodnoty, obdrží volaného ukazatel na kopii datovou strukturu.  
  
-   Pokud je třída nepřenositelné zařazena pomocí odkazu, obdrží volaného ukazatel na ukazatel na kopii datovou strukturu.  
  
-   Pokud <xref:System.Runtime.InteropServices.InAttribute> nastavený atribut, tato kopie je vždy inicializovat stavem instance zařazování podle potřeby.  
  
-   Pokud <xref:System.Runtime.InteropServices.OutAttribute> nastavený atribut, stav se vždy zkopíruje zpět na instanci na return zařazování podle potřeby.  
  
-   Pokud oba **InAttribute** a **OutAttribute** jsou nastavené, jsou požadovány obě kopie. Pokud je vynechán buď atribut, můžete optimalizovat zařazování odstraněním buď kopírování.  
  
## <a name="reference-types"></a>Typy odkazů  
 Hodnotou nebo odkazem, může být předán odkazové typy. Když jsou předávány podle hodnoty, je ukazatel typu předán v zásobníku. Při předání odkazem, je předaná ukazatel na ukazatel na typ na zásobníku.  
  
 Typy odkazů mít podmíněného následující chování:  
  
-   Pokud je předaná hodnota typu odkazu a má členy nepřenositelné typy, typy se převedou dvakrát:  
  
    -   Když je argument předaný nespravované straně.  
  
    -   Při návratu z volání.  
  
     Aby se zabránilo zbytečně kopírování a převodu tyto typy jsou zařazené jako v parametry. Musíte explicitně použít **InAttribute** a **OutAttribute** atributy pro argument volajícího a podívejte se změny provedené volaného.  
  
-   Pokud je předaná hodnota typu odkazu a má pouze členové přenositelné typy, může být připnutý při zařazování a všechny změny provedené volaného na členy typu jsou vidět volající. Použít **InAttribute** a **OutAttribute** explicitně, pokud chcete toto chování. Bez těchto směrovou atributů spolupráce vláken neexportuje směrovou informace ke knihovně typů (exportuje jako v, což je výchozí hodnota). to může způsobit problémy s zařazování mezi apartment COM.  
  
-   Pokud typ odkazu je předán odkazem, ji budou zařazována jako vstup/výstup ve výchozím nastavení.  
  
## <a name="systemstring-and-systemtextstringbuilder"></a>System.String a objektu System.Text.StringBuilder.  
 Pokud data je zařazen do nespravovaného kódu hodnotou nebo odkazem, zařazování obvykle zkopíruje data na sekundární vyrovnávací paměti (pravděpodobně převodu znakové sady během kopírování) a předá volaného odkaz do vyrovnávací paměti. Pokud je odkaz **BSTR** přidělený **SysAllocString**, odkaz na vždycky se přidělí s **CoTaskMemAlloc**.  
  
 Jako optimalizace když buď typ řetězce je zařazena pomocí hodnoty (například řetězec znaků Unicode), zařazování předá volaného přímé ukazatel na spravované řetězce v vnitřní vyrovnávací paměť Unicode namísto kopírování do nové vyrovnávací paměti.  
  
> [!CAUTION]
>  Pokud řetězec, je předaná hodnota, musí volaného nikdy změnit odkaz předaná zařazování. Díky tomu může dojít k poškození spravovaná halda.  
  
 Když <xref:System.String?displayProperty=nameWithType> je předán odkazem, zařazování zkopíruje obsah řetězec do vyrovnávací paměti sekundární před uskutečněním hovoru. Pak zkopíruje obsah vyrovnávací paměti do nového řetězce pro návrat z volání. Tento postup zajišťuje, že neměnné spravovaný řetězec zůstává beze změny.  
  
 Když <xref:System.Text.StringBuilder?displayProperty=nameWithType> je předaná hodnota, předává vláken a odkaz na vnitřní vyrovnávací paměť **StringBuilder** přímo na volající. Volající a volaný, musíte souhlasit na velikost vyrovnávací paměti. Volající zodpovídá za vytvoření **StringBuilder** odpovídající délky. Volaného nutné provést nezbytná opatření k zajištění, že není přetečení vyrovnávací paměti. **StringBuilder** je výjimkou pravidla, která odkazové typy předaná hodnota jsou předány jako parametry ve výchozím nastavení. Je to vždy předáno jako vstup/výstup.  
  
## <a name="see-also"></a>Viz také  
 [Výchozí chování zařazování](default-marshaling-behavior.md)  
 [Správa paměti s spolupráce zařazování vláken](https://msdn.microsoft.com/library/417206ce-ee3e-4619-9529-0c0b686c7bee(v=vs.100))  
 [Směrovou atributy](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))  
 [Zařazování spolupráce](interop-marshaling.md)
