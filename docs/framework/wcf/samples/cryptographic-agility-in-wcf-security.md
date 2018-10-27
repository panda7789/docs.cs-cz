---
title: Kryptografická flexibilita v zabezpečení WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 9f7c1157c9bf4f2e0baf7dcbafbcc9fca4aee89d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187332"
---
# <a name="cryptographic-agility-in-wcf-security"></a>Kryptografická flexibilita v zabezpečení WCF
Tato ukázka předvádí, jak určit v algoritmu standardní nebo vlastní poskytují kryptografické agilní implementace klienta Windows Communication Foundation (WCF) a služby. Ukázka se skládá z následující projekty:

 Služby, to je v místním prostředí služby WCF, který implementuje `ICalculator` rozhraní a zabezpečuje pomocí koncového bodu <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> zabezpečenou relaci a stabilní relaci zakázán. Služba definuje vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.

 Klient jedná WCFclient, který službu používá po úspěšném ověření. Vyvolá operace vystavené `ICalculator` rozhraní a službou implementována. Klient také definuje stejné vlastní `SecurityAlgorithmSuite` tak, aby určovala kryptografické algoritmy pro zabezpečení zpráv.

### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1.  Otevřete CryptoAgility.sln řešení v sadě Visual Studio 2012.

2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.

3.  Otevřít [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] a přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Service\bin a spusťte soubor service.exe s oprávněními správce tak, že service.exe kliknete pravým tlačítkem a vyberete **spustit jako správce**.

4.  Přejděte do adresáře \WCF\Basic\Security\CryptoAgility\Client\bin a spusťte soubor client.exe normálně.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení](../../../../docs/framework/wcf/feature-details/security.md)
