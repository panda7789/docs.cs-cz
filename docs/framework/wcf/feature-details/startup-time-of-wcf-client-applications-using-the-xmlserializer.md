---
title: 'Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 6f61c57998cfc21b66f278a1a2381407ec2c39ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer
Služby a klientské aplikace používající typy dat, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilace kódu serializace pro tyto typy dat za běhu, což může vést k pomalé spuštění výkonu.  
  
> [!NOTE]
>  Předem vygenerovaná serializace kódu je možné pouze v klientských aplikacích a není v služby.  
  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lze vylepšit výkon spuštění pro tyto aplikace generování kódu nezbytné serializace z kompilované sestavení pro aplikaci. Svcutil.exe generuje kód serializace pro všechny typy dat používané v kontraktech služby v sestavení kompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>. Služby a operace kontrakty, které používají <xref:System.Xml.Serialization.XmlSerializer> jsou označené <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Generování kódu serializace třídy XmlSerializer  
  
1.  Kompilaci kódu služba nebo klienta do jednoho nebo více sestavení.  
  
2.  Otevřete příkazový řádek SDK.  
  
3.  Na příkazovém řádku spusťte nástroje Svcutil.exe v následujícím formátu.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Argument určuje cestu k sestavení, který obsahuje typy kontraktů služby. Svcutil.exe generuje kód serializace pro všechny typy dat používané v kontraktech služby v sestavení kompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe mohou generovat jenom serializace kód C#. Jeden souboru zdrojového kódu se generuje pro každý vstupní sestavení. Nelze použít **/language** přepínač tak, aby změnit jazyk generovaného kódu.  
  
     Pokud chcete zadat cestu k závislá sestavení, použijte **/reference** možnost.  
  
4.  Kód vygenerovaný serializace zpřístupnit do vaší aplikace pomocí jedné z následujících možností:  
  
    1.  Zkompilovat kód vygenerovaný serializace do samostatné sestavení s názvem [*původní sestavení*]. XmlSerializers.dll (například MyApp.XmlSerializers.dll). Aplikace musí být schopen načíst sestavení, které musí být podepsané stejným klíčem jako původní sestavení. Pokud jste znovu zkompiluje původní sestavení, je třeba znovu vygenerovat sestavení serializace.  
  
    2.  Zkompilovat kód vygenerovaný serializace do samostatné sestavení a použít <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> na kontrakt služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Nastavte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti tak, aby odkazoval na sestavení kompilované serializace.  
  
    3.  Kód vygenerovaný serializace kompilována sestavení vaší aplikace a přidat <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> servisní smlouvou, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Nenastavujte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti. Výchozí serializace sestavení se předpokládá, že se aktuální sestavení.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Ke generování XmlSerializer serializace kódu v sadě Visual Studio  
  
1.  Vytvoření klienta a služby WCF projekty v sadě Visual Studio. Potom přidáte odkaz na službu do projektu klienta.  
  
2.  Přidat <xref:System.ServiceModel.XmlSerializerFormatAttribute> servisní smlouvou v *reference.cs* souboru v projekt klientské aplikace za **serviceReference** -> **reference.svcmap** . Všimněte si, že potřebujete zobrazit všechny soubory v **Průzkumníku řešení** zobrazíte tyto soubory.  
  
3.  Sestavení klientské aplikace.  
  
4.  Použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vytvoření předem vygenerovaných serializátoru *.cs* souboru pomocí příkazu:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     AssemblyPath argument určuje cestu k sestavení klienta WCF.  
  
     Například:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     *WCFClient.XmlSerializers.dll.cs* soubor bude vytvořen.  
  
5.  Kompilace sestavení předem vygenerovaná serializace.  
  
     Založena na příkladu v předchozím kroku, příkaz compile by být následující:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Zajistěte, aby vygenerovaného *WCFClient.XmlSerializers.dll* je ve stejném adresáři jako klientskou aplikaci, která je *WCFClient.exe* v tomto případě.  
  
6.  Spusťte klientskou aplikaci jako obvykle. Sestavení předem vygenerovaná serializace se použije.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří typy serializace pro `XmlSerializer` typy, které jakoukoli službu, měnící používán sestavení.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
