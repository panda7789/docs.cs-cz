---
title: 'Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: f8766a5dfa2bcfc715a0f0e21274f7c6ac04ad15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944897"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Postupy: Vylepšení doby spouštění klientských aplikací WCF pomocí třídy XmlSerializer
Služby a klientské aplikace, které používají datové typy, které jsou serializovatelný <xref:System.Xml.Serialization.XmlSerializer> pomocí generování a kompilování serializace kódu pro tyto datové typy za běhu, což může vést k pomalému spuštění výkonu.  
  
> [!NOTE]
> Předem generovaný kód serializace lze použít pouze v klientských aplikacích, nikoli v službách.  
  
 Nástroj pro měření [metadat třídy (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) může zlepšit výkon spuštění těchto aplikací vygenerováním potřebného kódu serializace z kompilovaných sestavení pro aplikaci. Svcutil. exe generuje kód serializace pro všechny datové typy používané v rámci kontraktů služby v sestavení zkompilované aplikace, které lze serializovat <xref:System.Xml.Serialization.XmlSerializer>pomocí. Kontrakty služeb a operace, které <xref:System.Xml.Serialization.XmlSerializer> používají, jsou označeny <xref:System.ServiceModel.XmlSerializerFormatAttribute>atributem.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Pro generování kódu serializace XmlSerializer  
  
1. Zkompilujte kód služby nebo klienta do jednoho nebo více sestavení.  
  
2. Otevřete příkazový řádek sady SDK.  
  
3. Na příkazovém řádku spusťte nástroj Svcutil. exe v následujícím formátu.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     `assemblyPath` Argument určuje cestu k sestavení, které obsahuje typy kontraktů služby. Svcutil. exe generuje kód serializace pro všechny datové typy používané v rámci kontraktů služby v sestavení zkompilované aplikace, které lze serializovat <xref:System.Xml.Serialization.XmlSerializer>pomocí.  
  
     Svcutil. exe může generovat C# pouze Serializační kód. Jeden soubor zdrojového kódu je vygenerován pro každé vstupní sestavení. Nelze použít přepínač **/Language** ke změně jazyka generovaného kódu.  
  
     Chcete-li zadat cestu k závislým sestavením, použijte možnost **/reference** .  
  
4. Zpřístupněte generovaný kód serializace vaší aplikaci pomocí jedné z následujících možností:  
  
    1. Zkompilujte generovaný kód serializace do samostatného sestavení s názvem [*původní sestavení*]. XmlSerializers. dll (například MyApp. XmlSerializers. dll). Vaše aplikace musí být schopna načíst sestavení, které musí být podepsáno stejným klíčem jako původní sestavení. Pokud znovu zkompilujete původní sestavení, je nutné znovu vygenerovat sestavení serializace.  
  
    2. Zkompilujte generovaný kód serializace do samostatného sestavení a použijte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> v kontraktu služby, který <xref:System.ServiceModel.XmlSerializerFormatAttribute>používá. Nastavte vlastnosti <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> nebo tak, aby odkazovaly na zkompilované sestavení serializace. <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A>  
  
    3. Zkompilujte generovaný kód serializace do sestavení aplikace a přidejte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> do kontraktu služby, který <xref:System.ServiceModel.XmlSerializerFormatAttribute>používá. Nenastavte <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> vlastnosti ani <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> . Výchozí sestavení serializace je považováno za aktuální sestavení.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Generování kódu serializace XmlSerializer v aplikaci Visual Studio  
  
1. Vytvořte v aplikaci Visual Studio službu WCF a klientské projekty. Pak přidejte odkaz na službu do klientského projektu.  
  
2.  -> Dosouboru *reference.cs* v projektu klientské aplikace v části **serviceReference** **reference. svcmap**přidejte dokontraktuslužby.<xref:System.ServiceModel.XmlSerializerFormatAttribute> Všimněte si, že je třeba zobrazit všechny soubory v **Průzkumník řešení** pro zobrazení těchto souborů.  
  
3. Sestavte klientskou aplikaci.  
  
4. Pomocí [nástroje Svcutil. exe (ServiceModel Metadata Utility)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vytvořte předem vygenerovaný soubor *. cs* pomocí příkazu:  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     Argument assemblyPath Určuje cestu k sestavení klienta WCF.  
  
     Například:  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     Vygeneruje se soubor *WCFClient.XmlSerializers.dll.cs* .  
  
5. Zkompilujte předem vygenerované sestavení serializace.  
  
     V závislosti na příkladu v předchozím kroku by příkaz Compile byl následující:  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Ujistěte se, že vygenerovaná *WCFClient. XmlSerializers. dll* je ve stejném adresáři jako klientská aplikace, která v tomto případě je *WCFClient. exe* .  
  
6. Spusťte aplikaci klienta obvyklým způsobem. Použije se předem vygenerované sestavení serializace.  
  
## <a name="example"></a>Příklad  
 Následující příkaz vytvoří typy serializace pro `XmlSerializer` typy, které používají všechny kontrakty služby v sestavení.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroj metadat modelu služby (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
