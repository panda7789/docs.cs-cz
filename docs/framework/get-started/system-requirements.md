---
title: "Požadavky na systém rozhraní .NET framework"
description: "Zjistěte, co jsou hardware, operační systém a softwarové požadavky pro instalaci rozhraní .NET Framework 4.5 a novější verze."
ms.custom: updateeachrelease
ms.date: 02/02/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a0cfbcbc4c2c0857c1fe4163484a43f4521444a3
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="net-framework-system-requirements"></a>Požadavky na systém rozhraní .NET framework

V tabulkách v tomto tématu najdete hardwaru, operačního systému a požadavky na software pro následující verze rozhraní .NET Framework:

* Rozhraní .NET framework 4.5 a jeho bod uvolní (4.5.1 a 4.5.2).
* Rozhraní .NET framework 4.6 a jeho bod uvolní (4.6.1 a 4.6.2).
* 4.7 rozhraní .NET framework a její verze bodu (4.7.1).

Vývojové prostředí, které vám umožní vyvíjet aplikace pro rozhraní .NET Framework mít samostatnou sadu požadavků.

> [!IMPORTANT]
> Vzhledem k tomu, že jsou na místě aktualizace rozhraní .NET Framework 4 všechny verze rozhraní .NET Framework, takže jenom na jedné 4.x verzi mohou existovat v systému.
> Kromě toho jsou nainstalovány na některé verze operačního systému Windows konkrétní verze rozhraní .NET Framework. To znamená, že:
>
> * Pokud je v počítači již nainstalována novější verze, nelze nainstalovat předchozí verze 4.x.
> * Pokud se na konkrétní verzi rozhraní .NET předem nainstalovaný operační systém, nelze nainstalovat předchozí verze 4.x na stejném počítači.
> * Pokud nainstalujete novější verzi, nemusíte nejdřív odinstalovat předchozí verzi.

Informace o stažení a odkazů najdete v tématu [instalaci rozhraní .NET Framework pro vývojáře](../../../docs/framework/install/guide-for-developers.md).

Informace o životním cyklu podpory rozhraní .NET Framework verze, najdete v části [životní cyklus podpory Microsoft](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Požadavky na hardware

|                          |        |
| ------------------------ | ------ |
| **Procesor**            | 1 GHz  |
| **PAMĚŤ RAM**                  | 512 MB |
| **Místo na disku (minimálně)** |        |
| 32bitová                   | 4.5 GB |
| 64bitových                   | 4.5 GB |

## <a name="installation-requirements"></a>Požadavky na instalaci

Rozhraní .NET Framework vyžaduje oprávnění správce pro instalaci. Pokud nemáte práva správce k počítači, kam chcete nainstalovat rozhraní .NET Framework, obraťte se na správce sítě.

## <a name="supported-client-operating-systems"></a>Podporované klientské operační systémy

| Operační systém | Podporované edice | Předinstalována s operačním systémem | Instalovat samostatně |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows 10 Fall Creators Update | 32bitová verze a 64bitová verze | Rozhraní .NET framework 4.7.1 | |
| Windows 10 Creators Update | 32bitová verze a 64bitová verze | Rozhraní .NET framework 4.7 | Rozhraní .NET framework 4.7.1 | 
| Windows 10 Anniversary Update | 32bitová verze a 64bitová verze | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|Rozhraní .NET framework 4.7<br/><br/>Rozhraní .NET framework 4.7.1 |
| Windows 10 November Update | 32bitová verze a 64bitová verze | .NET Framework 4.6.1 | .NET Framework 4.6.2 |
| Windows 10 | 32bitová verze a 64bitová verze | .NET Framework 4.6 | .NET Framework 4.6.1 <br/><br/> .NET Framework 4.6.2 |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32bitové, 64bitové a ARM | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />Rozhraní .NET framework 4.7<br/><br/>Rozhraní .NET framework 4.7.1 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32bitové, 64bitové a ARM | [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| Windows 7 SP1|32bitová verze a 64bitová verze | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />Rozhraní .NET framework 4.7<br/><br/>Rozhraní .NET framework 4.7.1|
| Windows Vista SP2|32bitová verze a 64bitová verze | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |
| Windows XP |32bitová verze a 64bitová verze | -- | .NET Framework 4 |

 **Poznámky:**

- V systémech Windows 7 se vyžaduje rozhraní .NET Framework Windows 7 SP1. Pokud jste v systému Windows 7 a aktualizací Service Pack 1 ještě nenainstalovali, budete muset učinit před instalací rozhraní .NET Framework.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Je podporována v prostředí Windows Preinstallation Environment (Windows PE). Ne všechny funkce podporované v prostředí Windows PE.

- Rozhraní .NET Framework 4 podporuje také platformě IA64.

- Pro všechny platformy, doporučujeme upgradovat na nejnovější aktualizaci Service Pack pro Windows a nainstalovat důležité aktualizace, které jsou k dispozici [webu Windows Update](http://go.microsoft.com/fwlink/?LinkId=168461) k zajištění nejvyšší kompatibility a zabezpečení.

- V 64bitových operačních systémech podporuje rozhraní .NET Framework WOW64 (32bitová verze zpracování na počítači 64-bit) a nativní 64bitové zpracování.

## <a name="supported-server-operating-systems"></a>Podporované serverové operační systémy

| Operační systém | Podporované edice | Předinstalována s operačním systémem | Instalovat samostatně |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Windows Server, version 1709 | 64bitových | Rozhraní .NET framework 4.7.1 | -- |
| Windows Server 2016 | 64bitových | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] | Rozhraní .NET framework 4.7<br/><br/> Rozhraní .NET framework 4.7.1 |
| Windows Server 2012 R2 | 64bitových | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />Rozhraní .NET framework 4.7<br/><br/> Rozhraní .NET framework 4.7.1 |
| Windows Server 2012 (64bitová verze) | 64bitových| [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />Rozhraní .NET framework 4.7<br/><br/>Rozhraní .NET framework 4.7.1 |
| Windows Server 2008 R2 SP1|64bitových | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />Rozhraní .NET framework 4.7<br/><br/>Rozhraní .NET framework 4.7.1 |
| Windows Server 2008 SP2|32bitová verze a 64bitová verze | -- | .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |

 **Poznámky:**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] zahrnuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], takže nemusíte instalovat samostatně. Podobně [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] zahrnuje [!INCLUDE[net_v451](../../../includes/net-v451-md.md)].

- Rozhraní .NET Framework má omezenou podporu pro Role Server Core s Windows Server 2008 R2 SP1 nebo novější. V tématu [funkce .NET serveru jádra](https://msdn.microsoft.com/library/ee391632.aspx) seznam nepodporované rozhraní API.

- Rozhraní .NET Framework není podporována v systému Windows Server 2008 R2 pro procesory Itanium.

- Na Windows Server 2008 SP2 nepodporuje rozhraní .NET Framework Server Core Role.

- Pro všechny platformy, doporučujeme, abyste upgrade na nejnovější aktualizaci Service Pack pro Windows a kritické aktualizace dostupné na [webu Windows Update](http://go.microsoft.com/fwlink/?LinkId=168461) k zajištění nejvyšší kompatibility a zabezpečení. U některých operačních systémů může být nutné instalovat nejnovější aktualizaci Service Pack pro Windows.

- V 64bitových operačních systémech podporuje rozhraní .NET Framework WOW64 (32bitová verze zpracování na počítači 64-bit) a nativní 64bitové zpracování.

## <a name="see-also"></a>Viz také

[Průvodce instalací](../../../docs/framework/install/index.md)   
[Začínáme](../../../docs/framework/get-started/index.md)   
[Řešení potíží se zablokovanými instalacemi a odinstalacemi rozhraní .NET Framework](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
