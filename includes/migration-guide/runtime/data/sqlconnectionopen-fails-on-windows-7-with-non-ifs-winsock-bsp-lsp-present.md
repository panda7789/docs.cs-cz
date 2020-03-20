---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803175"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open selže v systému Windows 7 s non-IFS Winsock BSP nebo LSP přítomen

|   |   |
|---|---|
|Podrobnosti|<xref:System.Data.SqlClient.SqlConnection.Open>a <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> selhání v rozhraní .NET Framework 4.5, pokud jsou v počítači spuštěny v počítači se systémem Windows 7 s rozhraním BSP nebo LSP, které nejsou službou IFS Winsock. Chcete-li zjistit, zda je nainstalován a) je <code>netsh WinSock Show Catalog</code> nainstalován a neifs bsp nebo LSP, použijte příkaz a zkontrolujte každou <code>Winsock Catalog Provider Entry</code> položku, která je vrácena. Pokud má hodnota Příznaky <code>0x20000</code> služby nastavený bit, poskytovatel použije popisovače IFS a bude pracovat správně. Pokud <code>0x20000</code> je bit čistý (není nastaven), jedná se o neIFS BSP nebo LSP.|
|Návrh|Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže se jí lze vyhnout upgradem rozhraní .NET Framework. Alternativně se tomu lze vyhnout odebráním všech nainstalovaných lsp rozhraní LSP bez rozhraní IFS Winsock.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
