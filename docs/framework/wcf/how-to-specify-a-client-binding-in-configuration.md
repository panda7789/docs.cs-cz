---
title: 'Postupy: Určení klientské vazby v konfiguraci'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 633bb0feeb0f9354bd6ff8ee6637f123d3e3cbf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928931"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Postupy: Určení klientské vazby v konfiguraci
V tomto příkladu se vytvoří konzolovou aplikaci klienta pro použití kalkulačky služby a vazby pro tohoto klienta je deklarativně zadaný v konfiguraci. Klient přistupuje k `CalculatorService`, která implementuje `ICalculator` rozhraní a službě i klientovi použít <xref:System.ServiceModel.BasicHttpBinding> třídy.  
  
 Podle uvedeného postupu se předpokládá, že je spuštěna služba kalkulačku. Informace o tom, jak sestavit službu, naleznete v tématu [jak: Zadání vazby služby v konfiguraci](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Využívá také [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , Windows Communication Foundation (WCF) poskytuje klientské součásti budou automaticky generovány. Nástroj vygeneruje kód klienta a konfigurace přístupu ke službě.  
  
 Klient je vytvořená ve dvou částech. Generuje svcutil.exe `ClientCalculator` , který implementuje `ICalculator` rozhraní. Tato klientská aplikace pak konstruován tak, že vytváří instanci `ClientCalculator`.  
  
 Obvykle je osvědčeným postupem určete vazbu a informace o adrese deklarativně v konfiguraci, nikoli imperativně v kódu. Definování koncových bodů v kódu není obvykle praktické protože vazeb a adresy pro službu nasazenou se obvykle liší od nastavení použít, je vyvíjena služby. Obecně platí udržování vazby a adresování informace mimo kód jim umožňuje změnit bez nutnosti znovu kompilovat nebo znovu nasadit aplikaci.  
  
 Všechny následující kroky konfigurace můžete provádět pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Pro zdrojovou kopii tohoto příkladu, najdete v článku [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) vzorku.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Zadání klientské vazby v konfiguraci  
  
1. Pomocí Svcutil.exe lze generovat kód z metadat služby z příkazového řádku.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Klient, který je generován obsahuje `ICalculator` rozhraní, které definuje kontrakt služby, který musí splňovat implementace klienta.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Také obsahuje implementaci generovaného klienta `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe také generuje konfiguraci pro klienta, který se používá <xref:System.ServiceModel.BasicHttpBinding> třídy. Když pomocí sady Visual Studio, název tohoto souboru App.config. Všimněte si, že adresa a informace o vazbě nejsou zadané kdekoli uvnitř implementace služby. Kód také, není nutné zapsat, aby načítal příslušné informace z konfiguračního souboru.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. Vytvoření instance `ClientCalculator` v aplikaci a potom volání operací služby.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Kompilace a spuštění klienta.  
  
## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
