---
title: 'Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: fb98919fe6d0ec67e5fea8c483e4993f2632267f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503127"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer
Služby a klientské aplikace, které používají datové typy, které jsou serializovatelné pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilaci kódu serializace pro typy dat za běhu, což může vést k pomalé spouštění výkonu.  
  
> [!NOTE]
>  Předem generovaného Serializační kód jde použít jenom v klientských aplikacích a ne v služeb.  
  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) výkon lze zvýšit objem požadovaný při spuštění pro tyto aplikace generování kódu serializace nezbytné ze zkompilovaných sestavení pro aplikaci. Generuje kód serializace pro všechny datové typy používané v kontraktech služeb v sestavení kompilované aplikace, které lze serializovat pomocí svcutil.exe <xref:System.Xml.Serialization.XmlSerializer>. Služby a operace smluv, které používají <xref:System.Xml.Serialization.XmlSerializer> jsou označené <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Ke generování kódu serializace XmlSerializer  
  
1.  Kompilaci kódu služby ani klienta do jednoho nebo více sestavení.  
  
2.  Otevřete příkazový řádek sady SDK.  
  
3.  Na příkazovém řádku spusťte nástroje Svcutil.exe v následujícím formátu.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Argument určuje cestu k sestavení, který obsahuje typy kontraktů služby. Generuje kód serializace pro všechny datové typy používané v kontraktech služeb v sestavení kompilované aplikace, které lze serializovat pomocí svcutil.exe <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe lze generovat C# Serializační kód. Jeden soubor zdrojového kódu se generuje pro každý vstupní sestavení. Nelze použít **/language** přepínači změnit jazyk generovaného kódu.  
  
     Chcete-li zadat cestu k závislá sestavení, použijte **/reference** možnost.  
  
4.  Kód vygenerovaný serializace zpřístupnit do vaší aplikace pomocí jedné z následujících možností:  
  
    1.  Kompilace generovaného Serializační kód do samostatné sestavení s názvem [*původní sestavení*]. XmlSerializers.dll (například MyApp.XmlSerializers.dll). Aplikace musí být schopný načíst sestavení, které musí být podepsané stejným klíčem jako původní sestavení. Pokud je provedena rekompilace původní sestavení, je třeba znovu vygenerovat sestavení serializace.  
  
    2.  Kompilace generovaného Serializační kód do samostatné sestavení a použít <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> v kontraktu služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Nastavte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti tak, aby odkazoval na kompilované serializace sestavení.  
  
    3.  Kompilace generovaného Serializační kód do vašeho sestavení aplikace a přidat <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> pro servisní smlouvy, které používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Nenastavujte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti. Výchozí sestavení serializace je považován za aktuální sestavení.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Ke generování kódu serializace XmlSerializer v sadě Visual Studio  
  
1.  Vytvoření klienta a služby WCF projekty v sadě Visual Studio. Nakonec přidejte odkaz na službu do projektu klienta.  
  
2.  Přidat <xref:System.ServiceModel.XmlSerializerFormatAttribute> ke kontraktu služby ve *reference.cs* soubor v projektu aplikace klienta v části **serviceReference** -> **reference.svcmap** . Všimněte si, že potřebujete zobrazit všechny soubory v **Průzkumníka řešení** zobrazíte tyto soubory.  
  
3.  Vytvořte klientskou aplikaci.  
  
4.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření předem generovaného serializátoru *.cs* soubor pomocí příkazu:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     AssemblyPath argument určuje cestu k sestavení klienta WCF.  
  
     Například:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* vygeneruje soubor.  
  
5.  Kompilace sestavení serializace předem generovaného.  
  
     Na základě příkladu v předchozím kroku, příkaz compile by byl následující:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Ujistěte se, že generované *WCFClient.XmlSerializers.dll* je ve stejném adresáři jako klientskou aplikaci, která je *WCFClient.exe* v tomto případě.  
  
6.  Spuštění klientské aplikace jako obvykle. Sestavení serializace předem generovaného se použije.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vygeneruje typy serializace pro `XmlSerializer` typy, které službám smluv týkajících se použití sestavení.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Viz také:
- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
