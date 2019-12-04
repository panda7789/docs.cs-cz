---
title: Kryptografická flexibilita v zabezpečení WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714928"
---
# <a name="cryptographic-agility-in-wcf-security"></a>Kryptografická flexibilita v zabezpečení WCF

Tento příklad ukazuje, jak zadat standardní/vlastní algoritmus pro zajištění kryptografické implementace v Windows Communication Foundation (WCF) klienta a služby. Ukázka se skládá z následujících projektů:

**Service**

Toto je Samoobslužná služba WCF, která implementuje rozhraní `ICalculator` a zabezpečení koncového bodu pomocí <xref:System.ServiceModel.WSHttpBinding> se zakázanou zabezpečenou relací a spolehlivou relací. Služba definuje vlastní třídu `SecurityAlgorithmSuite` pro určení kryptografických algoritmů, které se mají použít pro zabezpečení zprávy.

**Klient**

Toto je klient služby WCF, který po úspěšném ověření přistupuje ke službě. Vyvolá operace vystavené rozhraním `ICalculator` a implementované službou. Klient také definuje stejnou vlastní třídu `SecurityAlgorithmSuite` pro určení kryptografických algoritmů, které se mají použít pro zabezpečení zpráv.

## <a name="to-use-this-sample"></a>Použití této ukázky

1. Otevřete řešení CryptoAgility. sln v aplikaci Visual Studio 2012.

2. Stisknutím kombinace kláves CTRL + SHIFT + B Sestavte řešení.

3. Otevřete Průzkumníka souborů a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor Service. exe s oprávněními správce tak, že kliknete pravým tlačítkem na Service. exe a vyberete **Spustit jako správce**.

4. Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a normálně spusťte soubor Client. exe.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Viz také:

- [Windows Communication Foundation zabezpečení](../feature-details/security.md)
