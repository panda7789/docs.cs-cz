---
ms.openlocfilehash: 65d9edc1e7377a86f8185ebf28bb5bee3a3f887d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235282"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open selhání ve Windows 7 s IFS Winsock BSP nebo LSP k dispozici

|   |   |
|---|---|
|Podrobnosti|<xref:System.Data.SqlClient.SqlConnection.Open> a <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> selhat v rozhraní .NET Framework 4.5, pokud běží na počítači s Windows 7 s IFS Winsock BSP nebo LSP jsou k dispozici v počítači. Chcete-li zjistit, jestli je nainstalovaná IFS BSP nebo LSP, použijte <code>netsh WinSock Show Catalog</code> příkaz a zkontrolujte každý <code>Winsock Catalog Provider Entry</code> položku, která je vrácena. Pokud má hodnota příznaků služby <code>0x20000</code> bitem, poskytovatele používá IFS popisovače a bude fungovat správně. Pokud <code>0x20000</code> bit vymazat (Nenastaveno), je IFS BSP nebo LSP.|
|Doporučení|Tato chyba byla opravena v rozhraní .NET Framework 4.5.2, takže lze se vyhnout upgradem rozhraní .NET Framework. Alternativně můžete se vyhnout tak, že odeberete všechny nainstalované bez - IFS Winsock LSP.|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
