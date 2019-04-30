---
title: 'Omezení rizik: Správa verzí produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7b435c6050cbb73abab3cb5980632be55dd08d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61871528"
---
# <a name="mitigation-product-versioning"></a>Omezení rizik: Správa verzí produktu
V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a později, Správa verzí produktu změnil z předchozích verzí rozhraní .NET Framework (rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2).  
  
## <a name="product-versioning-changes"></a>Změn správy verzí produktu  
 Tady jsou podrobné změny:  
  
- Hodnota `Version` položku v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíč byl změněn na `4.6.` *xxxxx* pro rozhraní .NET Framework 4.6 a jeho novější vydání a `4.7.` *xxxxx* pro. .NET Framework 4.7. V rozhraní .NET Framework 4.5, 4.5.1 a 4.5.2, má formát `4.5.` *xxxxx*.  
  
- Správa verzí souboru a produktů pro soubory rozhraní .NET Framework byl změněn z předchozích schéma vytváření verzí z `4.0.30319.x` k `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho novější vydání a `4.7.X.0` pro rozhraní .NET Framework 4.7 a jeho verze. Tyto nové hodnoty se zobrazí při zobrazení souboru **vlastnosti** po klepnutí pravým tlačítkem na soubor.  
  
- <xref:System.Reflection.AssemblyFileVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributy pro spravované sestavení mají <xref:System.Version> hodnoty ve formuláři `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho novější vydání a `4.7.X.0` pro rozhraní .NET Framework 4.7.  
  
- V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1 a 4.6.2, 4.7, <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost vrací řetězec opravenou verzi `4.0.30319.42000`. V rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2, vrátí řetězce verze ve formátu `4.0.30319.xxxxx` (například "4.0.30319.18010"). Všimněte si, že nedoporučujeme tak novou závislost na kód aplikace <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="handling-the-product-versioning-changes"></a>Zpracování změn správy verzí produktu  
 Obecně platí aplikace by měl záviset na doporučené postupy pro zjištění takové věci jako verzi modulu runtime rozhraní .NET Framework a v instalačním adresáři:  
  
- Pokud chcete zjistit verzi modulu runtime rozhraní .NET Framework, přečtěte si téma [jak: Zjištění nainstalovaných verzí rozhraní .NET Framework](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
- Určete instalační cestu pro rozhraní .NET Framework, použijte hodnotu `InstallPath` položku `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíč.  
  
    > [!IMPORTANT]
    >  Je název podklíče `NET Framework Setup`, nikoli `.NET Framework Setup`.  
  
- Chcete-li určit cestu k adresáři na rozhraní .NET Framework common language runtime, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metody.  
  
- Chcete-li získat verzi modulu CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metody.   Pro rozhraní .NET Framework 4 a jeho vydání (.NET Framework 4.5, 4.5.1, 4.5.2, a [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1 a 4.6.2, 4.7), vrátí řetězec `v4.0.30319`.  
  
## <a name="see-also"></a>Viz také:

- [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
