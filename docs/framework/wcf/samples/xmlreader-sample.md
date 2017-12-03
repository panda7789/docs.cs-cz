---
title: "Ukázka třídy XmlReader"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML Reader
ms.assetid: 60e5848d-7d9c-4ea5-bed9-22758c9ac16c
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b8fe20b1a5d65a011ec0315773eafd6b4dd6ade
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="xmlreader-sample"></a>Ukázka třídy XmlReader
Ukázka třídy XmlReader ukazuje zpracování textu zprávy pomocí <xref:System.Xml.XmlReader>. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje službu kalkulačky. Operace další služby `Sum`, byl přidán, přijme zprávu, která obsahuje pole hodnot přidat společně. Služba přečte zprávu pomocí <xref:System.Xml.XmlReader>.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Rozhraní kalkulačky zahrnuje operace služby s názvem `Sum` který přijme <xref:System.ServiceModel.Channels.Message> parametr, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
    [OperationContract]  
    Message Sum(Message message);  
}  
```  
  
 Klient přistupuje k `Sum` nejdříve vytvořením pole celočíselné hodnoty, pak vytvořením zprávu z pole a pak volání `Sum` metodu pomocí vytvořenou zprávu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
CalculatorClient client = new CalculatorClient();  
...  
// Call the Sum service operation.  
int[] values = { 1, 2, 3, 4, 5 };  
using (new OperationContextScope(client.InnerChannel))  
{  
    Message request = Message.CreateMessage(OperationContext.Current.OutgoingMessageHeaders.MessageVersion, "http://Microsoft.ServiceModel.Samples/ICalculator/Sum", values);  
    Message reply = client.Sum(request);  
    int sum = reply.GetBody<int>();  
  
    Console.WriteLine("Sum(1,2,3,4,5) = {0}", sum);  
}  
```  
  
 V rámci služby, provádění operace služby `Sum` přistupuje k pomocí tělo zprávy <xref:System.Xml.XmlReader> objektu k iteraci v rámci hodnoty tak, aby součet. <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> Metoda je volána pro přístup k textu zprávy, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
public int Sum(Message message)  
{  
    int sum = 0;  
    string text = "";  
  
    //The body of the message contains a list of numbers that are read  
    //directly using an XmlReader.  
    XmlReader body = message.GetReaderAtBodyContents ();  
    while (body.Read())  
    {  
        text = body.ReadString().Trim();  
        if (text.Length>0)  
        {  
            sum += Convert.ToInt32(text);  
        }  
    }  
    body.Close();  
    Message response = Message.CreateMessage(  
       "http://Microsoft.ServiceModel.Samples/ICalculator/SumResponse",  
       sum);  
    return response;  
}  
```  
  
 Když spustíte ukázku, požadavky a odpovědi operace se zobrazují v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Sum(1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\XmlReader`  
  
## <a name="see-also"></a>Viz také
