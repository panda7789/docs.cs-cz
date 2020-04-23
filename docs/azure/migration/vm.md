---
title: Migrace webové aplikace v ASP.NET do virtuálního počítače Azure
description: Naučte se migrovat webovou aplikaci v ASP.NET z místního prostředí na virtuální počítač Azure.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072121"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Migrace webové aplikace v ASP.NET na virtuální počítač Azure

Tento dokument poskytuje přehled o tom, jak migrovat webovou aplikaci v ASP.NET z místního prostředí na virtuální počítač Azure.

## <a name="quickstart"></a>Rychlý start

Zjistěte, jak vytvořit virtuální počítač a jak do něj publikovat aplikaci: [publikování na virtuálním počítači Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>Začínáme

Tyto kurzy ukazují kroky pro vytvoření (nebo migraci) virtuálního počítače, publikování webové aplikace a další úkoly, které mohou být požadovány pro podporu vaší aplikace v Azure.

- Vytvořte virtuální počítač pro aplikaci ASP.NET v Azure pomocí jedné z následujících možností:
  - [Vytvoření nového virtuálního počítače pro aplikace ASP.NET](https://go.microsoft.com/fwlink/?linkid=863237)
  - [Migrace stávajícího místního virtuálního počítače VMWare](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [Migrace stávajícího místního virtuálního počítače Hyper-V](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [Publikování aplikace pomocí sady Visual Studio](https://go.microsoft.com/fwlink/?linkid=863240)
- [Vytvoření zabezpečené virtuální sítě pro vaše virtuální počítače](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [Vytvoření kanálu CI/CD pro vaši aplikaci](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [Přechod na škálu virtuálních počítačů s vysokou dostupností a škálovatelností](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>Požadavky

### <a name="benefits"></a>Výhody

Virtuální počítače nabízejí nejjednodušší cestu k migraci aplikace z místního prostředí do cloudu. Umožňují replikovat stejné prostředí, které vaše aplikace používá místně, a zároveň odstranit nutnost udržovat si vlastní datová centra. Virtual Machine Scale Sets poskytovat vysokou dostupnost a škálovatelnost aplikací běžících v Virtual Machines.

### <a name="virtual-machine-size"></a>Velikost virtuálního počítače

Vyberte velikost virtuálního počítače a typ, který je nejlépe optimalizovaný pro vaše zatížení. Další informace najdete v tématu [velikosti pro virtuální počítače s Windows v Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).

### <a name="maintenance"></a>Údržba

Stejně jako v místním počítači zodpovídáte za údržbu a aktualizaci<sup>&#42;</sup>virtuálních počítačů. Pokud vaše aplikace může běžet v prostředí PaaS (Platform as a Service), jako je například [Azure App Service](https://docs.microsoft.com/azure/app-service/) nebo v [kontejneru](https://docs.microsoft.com/azure/app-service/containers/), které tuto potřebu odstraní.

*<sup>&#42;</sup> [automatické upgrady operačního systému pro Virtual Machine Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) jsou aktuálně k dispozici jako služba ve verzi Preview.*

### <a name="virtual-networks"></a>Virtuální sítě

Virtuální sítě Azure umožňují:

- Sestavení hybridní infrastruktury, kterou ovládáte
- Přineste si vlastní IP adresy a servery DNS
- Vytvoření izolovaného a vysoce zabezpečeného prostředí pro vaše aplikace
- Připojte svůj virtuální počítač k místní síti pomocí jedné z několika [možností připojení](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti) .
- Integrujte svůj virtuální počítač do místní sítě pomocí [ExpressRoute](https://azure.microsoft.com/services/expressroute/)

Informace o tom, jak začít, najdete v [dokumentaci k Virtual Network](https://docs.microsoft.com/azure/virtual-network/)

### <a name="active-directory"></a>Active Directory
Mnoho aplikací používá ke správě ověřování a správy identit službu Active Directory.

- Azure AD Connect umožňuje integrovat místní adresáře s Azure Active Directory. Informace o tom, jak začít, najdete v tématu [Integrace místních adresářů s Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).
- [ExpressRoute](https://azure.microsoft.com/services/expressroute/) také umožňuje vaší aplikaci přistupovat k místní službě Active Directory.

### <a name="sql-databases"></a>Databáze SQL

Pokud vaše aplikace používá místní databázi, aplikace ve výchozím nastavení nebude schopná mluvit na ni. Máte tyto možnosti:

- Nakonfigurujte hybridní síť, která umožňuje vaší aplikaci přístup k vaší databázi běžící místně.
- Migrujte svou databázi do Azure. Další informace najdete v tématu [migrace databáze SQL Server do Azure](sql.md).

### <a name="high-availability-and-scalability"></a>Vysoká dostupnost a škálovatelnost

#### <a name="virtual-machine-scale-sets"></a>Virtual Machine Scale Sets
Chcete mít jistotu, že je vaše aplikace vysoce dostupná a může škálovat, migrovat image virtuálního počítače do sady škálování virtuálních počítačů Azure, aby se zlepšila dostupnost a škálovatelnost vaší aplikace. VM Scale Sets poskytují možnost použít existující virtuální počítač, který jste už nakonfigurovali, nebo vytvořit kanál sestavení pro sestavení image s vaší aplikací.

Informace o tom, jak začít, najdete v tématu [nasazení aplikace ve službě Virtual Machine Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).

#### <a name="centralized-logging"></a>Centralizované protokolování
Při spuštění aplikace napříč několika instancemi zvažte ukládání protokolů do centralizovaného umístění, jako je například [Azure Storage](https://docs.microsoft.com/azure/storage/).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Migrace databáze SQL Serveru do Azure](sql.md)
