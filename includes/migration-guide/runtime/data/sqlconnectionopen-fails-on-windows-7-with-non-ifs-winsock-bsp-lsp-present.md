---
ms.openlocfilehash: a1db9916c69c5974191eb6108fb54a0d9ff060d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622040"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection. Open se nepovedlo ve Windows 7 s neifs Winsock BSP nebo LSP.

#### <a name="details"></a>Podrobnosti

<xref:System.Data.SqlClient.SqlConnection.Open>a <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> v počítači se systémem Windows 7 selže v .NET Framework 4,5, pokud je spuštěný počítač se systémem Windows 7, který není IFS Winsock BSP nebo LSP. Chcete-li zjistit, zda je nainstalováno neifs BSP nebo LSP, použijte <code>netsh WinSock Show Catalog</code> příkaz a zkontrolujte všechny <code>Winsock Catalog Provider Entry</code> vrácené položky. Pokud má hodnota příznaků služby <code>0x20000</code> nastaven bit, zprostředkovatel použije popisovač IFS a bude správně fungovat. Pokud <code>0x20000</code> je bit jasný (nenastavený), jedná se o NEIFS BSP nebo LSP.

#### <a name="suggestion"></a>Návrh

Tato chyba byla opravena v .NET Framework 4.5.2, takže se ji můžete vyhnout upgradem .NET Framework. Případně se můžete vyhnout odebráním všech nainstalovaných rozhraní Winsock LSP typu non-IFS.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
