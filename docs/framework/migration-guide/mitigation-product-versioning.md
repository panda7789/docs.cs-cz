---
title: "Zmírňující opatření: Správa verzí produktu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15648a3dfc115e55dd78eb1f074b9c4235b89f34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-product-versioning"></a>Zmírňující opatření: Správa verzí produktu
V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a novější, Správa verzí produktu se změnil z předchozích verzí rozhraní .NET Framework (rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2).  
  
## <a name="product-versioning-changes"></a>Změny Správa verzí produktu  
 Tady jsou podrobné změny:  
  
-   Hodnota `Version` položku v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíče se změnila na `4.6.` *xxxxx* pro rozhraní .NET Framework 4.6 a jeho verze bodu a `4.7.` *xxxxx* pro. NET Framework 4.7. V rozhraní .NET Framework 4.5 a 4.5.1, 4.5.2, měl formát `4.5.` *xxxxx*.  
  
-   Správa verzí souborů a produktu pro soubory rozhraní .NET Framework změnil ze starší verze schéma `4.0.30319.x` k `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho verze bodu a `4.7.X.0` 4.7 rozhraní .NET Framework a jeho bod uvolní. Zobrazí se tyto nové hodnoty při zobrazení souboru **vlastnosti** po pravým tlačítkem myši na soubor.  
  
-   <xref:System.Reflection.AssemblyFileVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributy pro spravovaná sestavení mít <xref:System.Version> hodnoty ve formuláři `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho verze bodu a `4.7.X.0` pro 4.7 rozhraní .NET Framework.  
  
-   V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 a 4.7, <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost vrací řetězec pevné verze `4.0.30319.42000`. V rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2, vrátí verze řetězce ve formátu `4.0.30319.xxxxx` (například "4.0.30319.18010"). Všimněte si, že nedoporučujeme trvá žádné nové závislosti kód aplikace <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost.  
  
### <a name="handling-the-product-versioning-changes"></a>Zpracování změny Správa verzí produktu  
 Obecně platí aplikace by měla závisí na doporučené postupy pro zjišťování prvků jako verzi modulu runtime rozhraní .NET Framework a instalační adresář:  
  
-   Pokud chcete zjistit verzi modulu runtime rozhraní .NET Framework, přečtěte si téma [postupy: určení rozhraní .NET Framework verze jsou nainstalované](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
-   Pokud chcete zjistit instalační cesta pro rozhraní .NET Framework, použijte hodnotu `InstallPath` položku v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíč.  
  
    > [!IMPORTANT]
    >  Název podklíče je `NET Framework Setup`, nikoli `.NET Framework Setup`.  
  
-   Chcete-li zjistit, cesta k adresáři modulu CLR rozhraní .NET Framework, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metoda.  
  
-   Chcete-li získat verze CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metoda.   Pro rozhraní .NET Framework 4 a jeho bod uvolní (rozhraní .NET Framework 4.5, 4.5.1, 4.5.2, a [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 a 4.7), vrátí řetězec `v4.0.30319`.  
  
## <a name="see-also"></a>Viz také  
 [Změny v modulu runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
 
