---
title: Migrace ASP.NET webové aplikace do virtuálního počítače Azure
description: Zjistěte, jak migrovat ASP.NET webovou aplikaci z místního do virtuálního počítače Azure.
ms.topic: how-to
ms.date: 11/15/2017
ms.openlocfilehash: cc9477de92e6105762636ed3a2241949e69ac8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "82072121"
---
# <a name="migrate-an-aspnet-web-application-to-an-azure-virtual-machine"></a>Migrace webové aplikace ASP.NET do virtuálního počítače Azure

Tento dokument poskytuje přehled o tom, jak migrovat ASP.NET webové aplikace z místního do virtuálního počítače Azure.

## <a name="quickstart"></a>Rychlý start

Přečtěte si, jak vytvořit virtuální počítač a publikovat do něj aplikaci: [Publikování na virtuálním počítači Azure](https://tutorials.visualstudio.com/aspnet-vm/intro)

## <a name="get-started"></a>Začínáme

Tyto kurzy ukazují kroky k vytvoření (nebo migraci) virtuálního počítače, publikování webové aplikace do něj a další úkoly, které mohou být nutné pro podporu vaší aplikace v Azure.

- Vytvořte virtuální počítač pro vaši ASP.NET aplikaci v Azure pomocí jedné z následujících možností:
  - [Vytvoření nového virtuálního počítače pro ASP.NET aplikace](https://go.microsoft.com/fwlink/?linkid=863237)
  - [Migrace existujícího místního virtuálního počítače VMWare](https://docs.microsoft.com/azure/migrate/tutorial-migrate-vmware)
  - [Migrace existujícího místního virtuálního počítače Hyper-V](https://docs.microsoft.com/azure/migrate/tutorial-migrate-hyper-v)
- [Publikování aplikace pomocí Visual Studia](https://go.microsoft.com/fwlink/?linkid=863240)
- [Vytvoření zabezpečené virtuální sítě pro virtuální počítače](https://docs.microsoft.com/azure/virtual-network/virtual-network-get-started-vnet-subnet)
- [Vytvoření kanálu CI/CD pro vaši aplikaci](https://docs.microsoft.com/vsts/build-release/apps/cd/deploy-webdeploy-iis-deploygroups)
- [Přechod na škálovací sadu virtuálních aplikací pro vysokou dostupnost a škálovatelnost](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app)

## <a name="considerations"></a>Požadavky

### <a name="benefits"></a>Výhody

Virtuální počítače nabízejí nejjednodušší cestu k migraci aplikace z místního do cloudu. Umožňují replikovat stejné prostředí, které vaše aplikace používá místně, a zároveň odstraňují potřebu udržovat vlastní datová centra. Škálovací sady virtuálních počítačů poskytují vysokou dostupnost a škálovatelnost pro aplikace spuštěné ve virtuálních počítačích.

### <a name="virtual-machine-size"></a>Velikost virtuálního počítače

Zvolte velikost a typ virtuálního počítače, který je nejlépe optimalizovaný pro vaši úlohu. Další informace najdete v [tématu Velikosti pro virtuální počítače s Windows v Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sizes).

### <a name="maintenance"></a>Údržba

Stejně jako místní počítač, jste zodpovědní za údržbu a aktualizaci<sup> virtuálního </sup>počítače&#42;. Pokud vaše aplikace může běžet v prostředí platformy jako služba (PaaS), jako je [například Azure App Service](https://docs.microsoft.com/azure/app-service/) nebo v [kontejneru](https://docs.microsoft.com/azure/app-service/containers/), která odebere tuto potřebu.

*<sup>&#42;</sup> [automatické upgrady operačního systému pro škálovací sady virtuálních strojů](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-automatic-upgrade) je v současné době k dispozici jako služba Preview.*

### <a name="virtual-networks"></a>Virtuální sítě

Virtuální sítě Azure umožňují:

- Vytvoření hybridní infrastruktury, kterou ovládáte
- Přineste si vlastní IP adresy a DNS servery
- Vytvoření izolovaného a vysoce zabezpečeného prostředí pro vaše aplikace
- Připojení virtuálního počítače k místní síti pomocí jedné z několika [možností připojení](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-about-vpngateways#s2smulti)
- Integrace virtuálního počítače do místní sítě pomocí [ExpressRoute](https://azure.microsoft.com/services/expressroute/)

Chcete-li začít, podívejte se na [dokumentaci k virtuální síti](https://docs.microsoft.com/azure/virtual-network/)

### <a name="active-directory"></a>Active Directory
Mnoho aplikací používá službu Active Directory pro ověřování a správu identit.

- Azure AD Connect umožňuje integrovat místní adresáře s Azure Active Directory. Informace o tom, jak začít, najdete [v tématu Integrace místních adresářů pomocí služby Azure Active Directory](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).
- Alternativně [ExpressRoute](https://azure.microsoft.com/services/expressroute/) umožňuje vaší aplikaci přístup k místní službě Active Directory.

### <a name="sql-databases"></a>Databáze SQL

Pokud vaše aplikace používá místní databázi, vaše aplikace nebude moct mluvit s ní ve výchozím nastavení. Máte tyto možnosti:

- Nakonfigurujte hybridní síť, která umožňuje vaší aplikaci přístup k databázi spuštěné místně.
- Migrujte databázi do Azure. Další informace najdete [v tématu Migrace databáze serveru SQL Server do Azure](sql.md).

### <a name="high-availability-and-scalability"></a>Vysoká dostupnost a škálovatelnost

#### <a name="virtual-machine-scale-sets"></a>Virtual Machine Scale Sets
Chcete se ujistit, že vaše aplikace je vysoce dostupná a může škálovat, migrovat image virtuálního počítače do škálovací sady virtuálních strojů Azure, abyste zlepšili dostupnost a škálovatelnost vaší aplikace. Škálovací sady virtuálních zařízení poskytují možnost používat existující virtuální počítač, který jste už nakonfigurovali, nebo nastavit kanál sestavení k vytvoření image s vaší aplikací.

Další informace najdete v [tématu Nasazení aplikace ve škálovacích sadách virtuálních strojů](https://docs.microsoft.com/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-deploy-app).

#### <a name="centralized-logging"></a>Centralizované protokolování
Při spuštění aplikace ve více instancích zvažte ukládání protokolů v centralizovaném umístění, jako je [Azure Storage](https://docs.microsoft.com/azure/storage/).

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Migrace databáze SQL Serveru do Azure](sql.md)
