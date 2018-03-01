---
title: "Postupy: Definování kontraktu služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c69f79d8629acee80a2e59346032e7733ec37dea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>Postupy: Definování kontraktu služby WCF
Toto je první šesti úkoly vyžadované pro vytvoření základní [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace. Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.  
  
 Při vytváření [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] je první úlohou služba, za účelem definování kontraktu služby. Kontrakt služby specifikuje, jaké operace služby podporuje. Operace můžete představit jako metodu webové služby. Kontrakty se vytvoří definováním rozhraní C++, C# nebo Visual Basic (VB). Každá metoda v rozhraní odpovídá konkrétní operaci služby. Každé rozhraní musí mít <xref:System.ServiceModel.ServiceContractAttribute> použije na ni a každou operace musí mít <xref:System.ServiceModel.OperationContractAttribute> byt aplikovaný atribut. Pokud metoda v rozhraní, které má <xref:System.ServiceModel.ServiceContractAttribute> atribut nemá <xref:System.ServiceModel.OperationContractAttribute> atribut, taková metoda se nevystaví službou.  
  
 Kód použitý pro tuto úlohu je najdete v příkladu za postupem.  
  
### <a name="to-define-a-service-contract"></a>K definování kontraktu služby  
  
1.  Otevřete [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako správce program pravým tlačítkem myši **spustit** nabídky a výběrem **spustit jako správce**.  
  
2.  Kliknutím na vytvořit projekt knihovny služby WCF **soubor** nabídky a výběrem **nový**, **projektu**. V **nový projekt** dialogu na levé straně dialogového okna rozbalte **Visual C#** pro projekt C# nebo **jiné jazyky** a potom **jazykaVisualBasic** pro projektu jazyka Visual Basic. V části jazyk vybraný vyberte **WCF** a zobrazí se seznam šablon projektu na části center dialogového okna. Vyberte **knihovny služby WCF**a typ `GettingStartedLib` v **název** textové pole a `GettingStarted` v **název řešení** textového pole v dolní části dialogového okna.  
  
3.  Visual Studio vytvoří projekt, který obsahuje soubory 3: IService1.cs (nebo IService1.vb) Service1.cs (nebo Service1.vb) a souboru App.config.  Soubor IService1 obsahuje výchozí smlouvy o poskytování služeb.  Soubor Service1 obsahuje výchozí implementace kontraktu služby. Soubor App.config obsahuje konfiguraci potřebné k načtení výchozí služba s Visual Studio hostitel služby WCF. Další informace o nástroji pro hostitele služeb WCF najdete v tématu [hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  Otevřete soubor IService1.cs nebo IService1.vb a odstraňte kód v deklaraci oboru názvů ponechat deklaraci oboru názvů. V oboru názvů deklarace definujte nové rozhraní nazývá `ICalculator` jak je znázorněno v následujícím kódu.  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
            public interface ICalculator  
            {  
                [OperationContract]  
                double Add(double n1, double n2);  
                [OperationContract]  
                double Subtract(double n1, double n2);  
                [OperationContract]  
                double Multiply(double n1, double n2);  
                [OperationContract]  
                double Divide(double n1, double n2);  
            }  
    }  
    ```  
  
    ```  
    ‘IService.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
        Public Interface ICalculator  
  
            <OperationContract()> _  
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
        End Interface  
    End Namespace  
    ```  
  
     Tento kontrakt definuje online kalkulačky. Upozornění `ICalculator` rozhraní je označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut. Tento atribut definuje obor názvů, který se používá k rozlišení názvu kontraktu. Každé operace kalkulačky je označené jako <xref:System.ServiceModel.OperationContractAttribute> atribut.  
  
    > [!NOTE]
    >  Při používání atributů k anotaci rozhraním, člen nebo třídy, můžete vložit část "Atribut" od názvu atributu. Proto <xref:System.ServiceModel.ServiceContractAttribute> stane `[ServiceContract]` v jazyce C# nebo `<ServiceContract>` v jazyce Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Postupy: Implementace kontraktu služby](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [Začínáme](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Vlastní hostování](../../../docs/framework/wcf/samples/self-host.md)
