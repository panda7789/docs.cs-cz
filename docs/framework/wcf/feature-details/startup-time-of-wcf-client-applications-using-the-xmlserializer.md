---
title: 'Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 91712963908ecc56ff17fbac028389207544b82f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600254"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer
Služby a klientské aplikace, které používají datové typy, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilování serializace kódu pro tyto datové typy za běhu, což může vést k pomalému spuštění výkonu.  
  
> [!NOTE]
> Předem generovaný kód serializace lze použít pouze v klientských aplikacích, nikoli v službách.  
  
 Nástroj pro měření [metadat třídy (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) může zlepšit výkon spuštění těchto aplikací vygenerováním potřebného kódu serializace z kompilovaných sestavení pro aplikaci. Svcutil. exe generuje kód serializace pro všechny datové typy používané v rámci kontraktů služby v sestavení zkompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer> . Kontrakty služeb a operace, které používají, <xref:System.Xml.Serialization.XmlSerializer> jsou označeny atributem <xref:System.ServiceModel.XmlSerializerFormatAttribute> .  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Pro generování kódu serializace XmlSerializer  
  
1. Zkompilujte kód služby nebo klienta do jednoho nebo více sestavení.  
  
2. Otevřete příkazový řádek sady SDK.  
  
3. Na příkazovém řádku spusťte nástroj Svcutil. exe v následujícím formátu.  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath`Argument určuje cestu k sestavení, které obsahuje typy kontraktů služby. Svcutil. exe generuje kód serializace pro všechny datové typy používané v rámci kontraktů služby v sestavení zkompilované aplikace, které lze serializovat pomocí <xref:System.Xml.Serialization.XmlSerializer> .  
  
     Svcutil. exe může generovat pouze kód serializace jazyka C#. Jeden soubor zdrojového kódu je vygenerován pro každé vstupní sestavení. Nelze použít přepínač **/Language** ke změně jazyka generovaného kódu.  
  
     Chcete-li zadat cestu k závislým sestavením, použijte možnost **/reference** .  
  
4. Zpřístupněte generovaný kód serializace vaší aplikaci pomocí jedné z následujících možností:  
  
    1. Zkompilujte generovaný kód serializace do samostatného sestavení s názvem [*původní sestavení*]. XmlSerializers. dll (například MyApp. XmlSerializers. dll). Vaše aplikace musí být schopna načíst sestavení, které musí být podepsáno stejným klíčem jako původní sestavení. Pokud znovu zkompilujete původní sestavení, je nutné znovu vygenerovat sestavení serializace.  
  
    2. Zkompilujte generovaný kód serializace do samostatného sestavení a použijte v <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kontraktu služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute> . Nastavte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> vlastnosti nebo <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> tak, aby odkazovaly na zkompilované sestavení serializace.  
  
    3. Zkompilujte generovaný kód serializace do sestavení aplikace a přidejte do <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> kontraktu služby, který používá <xref:System.ServiceModel.XmlSerializerFormatAttribute> . Nenastavte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> vlastnosti ani. Výchozí sestavení serializace je považováno za aktuální sestavení.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Generování kódu serializace XmlSerializer v aplikaci Visual Studio  
  
1. Vytvořte v aplikaci Visual Studio službu WCF a klientské projekty. Pak přidejte odkaz na službu do klientského projektu.  
  
2. Do <xref:System.ServiceModel.XmlSerializerFormatAttribute> souboru *reference.cs* v projektu klientské aplikace v části **serviceReference**  ->  **reference. svcmap**přidejte do kontraktu služby. Všimněte si, že je třeba zobrazit všechny soubory v **Průzkumník řešení** pro zobrazení těchto souborů.  
  
3. Sestavte klientskou aplikaci.  
  
4. Pomocí [nástroje Svcutil. exe (ServiceModel Metadata Utility)](../servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořte předem vygenerovaný soubor *. cs* pomocí příkazu:  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     Argument assemblyPath Určuje cestu k sestavení klienta WCF.  
  
     Například:  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     Vygeneruje se soubor *WCFClient.XmlSerializers.dll.cs* .  
  
5. Zkompilujte předem vygenerované sestavení serializace.  
  
     V závislosti na příkladu v předchozím kroku by příkaz Compile byl následující:  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Ujistěte se, že vygenerovaná *WCFClient. XmlSerializers. dll* je ve stejném adresáři jako klientská aplikace, která v tomto případě je *WCFClient. exe* .  
  
6. Spusťte aplikaci klienta obvyklým způsobem. Použije se předem vygenerované sestavení serializace.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří typy serializace pro `XmlSerializer` typy, které používají všechny kontrakty služby v sestavení.  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroj ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
