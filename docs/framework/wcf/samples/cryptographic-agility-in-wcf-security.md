---
title: Kryptografická flexibilita v zabezpečení WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: b8e3b6dc62baf31901520d7f5edac0529e937016
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490936"
---
# <a name="cryptographic-agility-in-wcf-security"></a>Kryptografická flexibilita v zabezpečení WCF

Tato ukázka předvádí, jak určit v algoritmu standardní nebo vlastní poskytují kryptografické agilní implementace klienta Windows Communication Foundation (WCF) a služby. Ukázka se skládá z následující projekty:

**Service**

Toto je v místním prostředí služby WCF, který implementuje `ICalculator` rozhraní a zabezpečuje pomocí koncového bodu <xref:System.ServiceModel.WSHttpBinding> zabezpečenou relaci a stabilní relaci zakázán. Služba definuje vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.

**Klient**

Toto je klienta WCF, který přistupuje k službě po úspěšném ověření. Vyvolá operace vystavené `ICalculator` rozhraní a službou implementována. Klient také definuje stejné vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.

## <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Otevřete CryptoAgility.sln řešení v sadě Visual Studio 2012.

2. Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.

3. Otevřete Průzkumníka souborů a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor service.exe s oprávněními správce tak, že service.exe kliknete pravým tlačítkem a vyberete **spustit jako správce**.

4. Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a spusťte soubor client.exe normálně.

> [!IMPORTANT]
> Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Viz také:

- [Zabezpečení Windows Communication Foundation](../feature-details/security.md)
