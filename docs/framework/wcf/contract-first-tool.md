---
title: Nástroj Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: b8d38cc31eacf1d8eb29aaaf7d6ef29056ff9b79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="contract-first-tool"></a>Nástroj Contract-First
Kontrakty služeb často potřebují vytvořena z existujících služeb. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], třídy kontraktu dat můžete automaticky vytvořen z existujících služeb pomocí nástroj contract-first. Pokud chcete používat nástroj contract-first, musí být soubor definice schématu XML (XSD) stažen místně; Nástroj nemůže importovat kontrakty vzdálených dat prostřednictvím protokolu HTTP.  
  
 Nástroj contract-first je integrována do [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] jako úlohu sestavení. Soubory kódu generovaných sestavovací úlohy jsou vytvořena pokaždé, když při vytváření projektu, tak, aby projekt můžete snadno použít změny v základní kontrakt služby.  
  
 Typy schémat, které můžete importovat nástroj contract-first zahrnují následující:  
  
```xml  
<xsd:complexType>  
<xsd:simpleType>  
```  
  
 Jednoduché typy nebude vygenerováno, pokud jsou například primitiv `Int16` nebo `String`; komplexní typy nebude vygenerováno, pokud jsou typu `Collection`. Typy nebude vygenerováno taky, pokud jsou součástí jiného `xsd:complexType`. V těchto případech se bude odkazovat typy k existujícím typům v projektu místo.  
  
## <a name="adding-a-data-contract-to-a-project"></a>Přidávání do projektu kontraktu dat  
 Před použitím nástroj contract-first kontrakt služby (XSD) je třeba přidat do projektu. Pro účely tohoto přehledu se použije pro ilustraci kontrakt první funkce následující kontrakt. Definice této služby je malou podmnožinu kontrakt služby používané vyhledávání na Bingu rozhraní API.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="ServiceSchema"  
    targetNamespace="http://tempuri.org/ServiceSchema.xsd"  
    elementFormDefault="qualified"  
    xmlns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:mstns="http://tempuri.org/ServiceSchema.xsd"  
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
>  
  <xs:complexType name="SearchRequest">  
    <xs:sequence>  
      <xs:element minOccurs="0" maxOccurs="1" name="Version" type="xs:string" default="2.2" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Market" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="UILanguage" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="Query" type="xs:string" />  
      <xs:element minOccurs="1" maxOccurs="1" name="AppId" type="xs:string" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Latitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Longitude" type="xs:double" />  
      <xs:element minOccurs="0" maxOccurs="1" name="Radius" type="xs:double" />  
    </xs:sequence>  
  </xs:complexType>  
  <xs:simpleType name="WebSearchOption">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="DisableHostCollapsing" />  
      <xs:enumeration value="DisableQueryAlterations" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
 Chcete-li přidat výše kontraktu služby do projektu, klikněte pravým tlačítkem na projekt a vyberte **přidat nové...** . Vyberte definice schématu z podokna WCF šablony dialogového okna a název nového souboru SampleContract.xsd. Zkopírujte a vložte kód výše do zobrazení kódu nové souboru.  
  
## <a name="configuring-contract-first-options"></a>Kontrakt první možnosti konfigurace  
 Kontrakt první možnosti, lze nastavit v nabídce vlastnosti [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu. Chcete-li vývoj s včasným kontrakt, vyberte **povolit XSD jako typ Definition Language** zaškrtnutí políčka na stránce WCF okna vlastností projektu.  
  
 ![Kontrakt zobrazující možnosti projektu WCF&#45;první](../../../docs/framework/wcf/media/contractfirstoptions.png "ContractFirstOptions")  
  
 Chcete-li nastavit upřesňující vlastnosti, klikněte na tlačítko Upřesnit.  
  
 ![Rozšířené kontrakt&#45;první vlastnosti](../../../docs/framework/wcf/media/contractfirstadvanced.png "ContractFirstAdvanced")  
  
 Následující upřesňující nastavení lze nakonfigurovat pro generování kódu ze smluv. Nastavení se dá nakonfigurovat jenom pro všechny soubory v projektu. u jednotlivých souborů v tuto chvíli nelze konfigurovat nastavení.  
  
-   **Serializátor režimu**: Toto nastavení určuje, které serializátor se používá k přečtení soubory kontrakt služby. Když **serializátoru XML** je vybrána, **typy kolekcí** a **znovu použít typy** možnosti jsou zakázány. Tyto možnosti se uplatní jenom na **serializátor kontraktu dat**.  
  
-   **Znovu použít typy**: Toto nastavení určuje, které knihovny se používají pro opakované použití typu. Toto nastavení platí pouze v případě **serializátor režimu** je nastaven na **serializátor kontraktu dat**.  
  
-   **Typ kolekce**: Toto nastavení určuje plně kvalifikovaný nebo sestavení kvalifikovaný typ má být použit pro datový typ kolekce. Toto nastavení platí pouze v případě **serializátor režimu** je nastaven na **serializátor kontraktu dat**.  
  
-   **Typ slovníku**: Toto nastavení určuje plně kvalifikovaný nebo sestavení kvalifikovaný typ má být použit pro datový typ slovníku.  
  
-   **EnableDataBinding**: Toto nastavení určuje, jestli se mají implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní pro všechny datové typy pro implementaci datové vazby.  
  
-   **ExcludedTypes**: Toto nastavení určuje seznam plně kvalifikovaný nebo kvalifikovaný sestavení typů, které mají být vyloučeny z odkazovaných sestaveních. Toto nastavení platí pouze v případě **serializátor režimu** je nastaven na **serializátor kontraktu dat**.  
  
-   **GenerateInternalTypes**: Toto nastavení určuje, jestli se má generovat třídy, které jsou označené jako vnitřní. Toto nastavení platí pouze v případě **serializátor režimu** je nastaven na **serializátor kontraktu dat**.  
  
-   **GenerateSerializableTypes**: Toto nastavení určuje, jestli se má generovat tříd pomocí <xref:System.SerializableAttribute> atribut. Toto nastavení platí pouze v případě **serializátor režimu** je nastaven na **serializátor kontraktu dat**.  
  
-   **ImportXMLTypes**: Toto nastavení určuje, zda chcete konfigurovat serializátor kontraktu dat pro použití <xref:System.SerializableAttribute> atribut tříd bez objektů <xref:System.Runtime.Serialization.DataContractAttribute> atribut.  Toto nastavení platí pouze v případě **serializátor režimu** je nastaven na **serializátor kontraktu dat**.  
  
-   **SupportFx35TypedDataSets**: Toto nastavení určuje, zda chcete poskytnout další funkce pro typové datové sady vytvořené pro rozhraní .net Framework 3.5. Když **serializátor režimu** je nastaven na **serializátoru XML**, <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> rozšíření se zařadí do – Importér schématu XML, když tato hodnota nastavena na hodnotu True. Když **serializátor režimu** je nastaven na **serializátor kontraktu dat**, typ <xref:System.DateTimeOffset> budou vyloučeny z odkazů, když tato hodnota nastavena na hodnotu False, tak, aby <xref:System.DateTimeOffset> se vždy vygeneruje pro starší verze framework.  
  
-   **InputXsdFiles**: Toto nastavení určuje seznam vstupních souborů. Každý soubor musí obsahovat platné schéma XML.  
  
-   **Jazyk**: Toto nastavení určuje jazyk kódu generovaného kontrakt. Nastavení musí být rozpoznatelném podle <xref:System.CodeDom.Compiler.CodeDomProvider>.  
  
-   **NamespaceMappings**: Toto nastavení určuje mapování z oborů názvů XSD cíl na obory názvů CLR. Každý mapování musí mít následující formát:  
  
    ```xml  
    "<Schema Namespace>, <CLR Namespace>"  
    ```  
  
     Serializátor XML lze zadat pouze jedno mapování v následujícím formátu:  
  
    ```xml  
    "*, <CLR Namespace>"  
    ```  
  
-   **Výstupnísložka**: Toto nastavení určuje adresář, kde se budou generovat soubory kódu.  
  
 Nastavení se použije při sestavení projektu generovat typy kontraktů služby z soubory kontrakt služby.  
  
## <a name="using-contract-first-development"></a>Pomocí vývoj s včasným kontraktu  
 Po přidání kontraktu služby do projektu a potvrzení nastavení sestavení, sestavení projektu stisknutím **F6**. Typy definované v kontrakt služby pak bude k dispozici pro použití v projektu.  
  
 Pokud chcete používat typy definované v kontrakt služby, přidejte odkaz na `ContractTypes` v aktuálním oboru názvů:  
  
```csharp  
using MyProjectNamespace.ContractTypes;  
```  
  
 Typy definované v kontrakt služby bude přeložit v projektu, jak je uvedeno níže.  
  
 ![Pomocí typy odvozené od kontraktu služby](../../../docs/framework/wcf/media/contractfirsttypes.png "ContractFirstTypes")  
  
 Typy generovaný nástrojem jsou vytvořeny v souboru GeneratedXSDTypes.cs. Soubor je vytvořen v \<adresáři projektu > /obj/\<konfigurace sestavení > /XSDGeneratedCode/ directory ve výchozím nastavení. Ukázka schématu na začátku tohoto tématu je převést následujícím způsobem:  
  
```csharp
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:4.0.30319.17330  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace TestXSD3.ContractTypes  
{  
    using System.Xml.Serialization;  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.ComponentModel.DesignerCategoryAttribute("code")]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=true)]  
    public partial class SearchRequest  
    {  
  
        private string versionField;  
  
        private string marketField;  
  
        private string uILanguageField;  
  
        private string queryField;  
  
        private string appIdField;  
  
        private double latitudeField;  
  
        private bool latitudeFieldSpecified;  
  
        private double longitudeField;  
  
        private bool longitudeFieldSpecified;  
  
        private double radiusField;  
  
        private bool radiusFieldSpecified;  
  
        public SearchRequest()  
        {  
            this.versionField = "2.2";  
        }  
  
        /// <remarks/>  
        [System.ComponentModel.DefaultValueAttribute("2.2")]  
        public string Version  
        {  
            get  
            {  
                return this.versionField;  
            }  
            set  
            {  
                this.versionField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Market  
        {  
            get  
            {  
                return this.marketField;  
            }  
            set  
            {  
                this.marketField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string UILanguage  
        {  
            get  
            {  
                return this.uILanguageField;  
            }  
            set  
            {  
                this.uILanguageField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string Query  
        {  
            get  
            {  
                return this.queryField;  
            }  
            set  
            {  
                this.queryField = value;  
            }  
        }  
  
        /// <remarks/>  
        public string AppId  
        {  
            get  
            {  
                return this.appIdField;  
            }  
            set  
            {  
                this.appIdField = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Latitude  
        {  
            get  
            {  
                return this.latitudeField;  
            }  
            set  
            {  
                this.latitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LatitudeSpecified  
        {  
            get  
            {  
                return this.latitudeFieldSpecified;  
            }  
            set  
            {  
                this.latitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Longitude  
        {  
            get  
            {  
                return this.longitudeField;  
            }  
            set  
            {  
                this.longitudeField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool LongitudeSpecified  
        {  
            get  
            {  
                return this.longitudeFieldSpecified;  
            }  
            set  
            {  
                this.longitudeFieldSpecified = value;  
            }  
        }  
  
        /// <remarks/>  
        public double Radius  
        {  
            get  
            {  
                return this.radiusField;  
            }  
            set  
            {  
                this.radiusField = value;  
            }  
        }  
  
        /// <remarks/>  
        [System.Xml.Serialization.XmlIgnoreAttribute()]  
        public bool RadiusSpecified  
        {  
            get  
            {  
                return this.radiusFieldSpecified;  
            }  
            set  
            {  
                this.radiusFieldSpecified = value;  
            }  
        }  
    }  
  
    /// <remarks/>  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Xml", "4.0.30319.17330")]  
    [System.SerializableAttribute()]  
    [System.Xml.Serialization.XmlTypeAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd")]  
    [System.Xml.Serialization.XmlRootAttribute(Namespace="http://tempuri.org/ServiceSchema.xsd", IsNullable=false)]  
    public enum WebSearchOption  
    {  
  
        /// <remarks/>  
        DisableHostCollapsing,  
  
        /// <remarks/>  
        DisableQueryAlterations,  
    }  
}  
```  
  
## <a name="errors-and-warnings"></a>Chyby a upozornění  
 Chyby a upozornění došlo při analýze schématu XSD zobrazí tak, jak sestavit chyby a upozornění.  
  
## <a name="interface-inheritance"></a>Rozhraní dědičnosti  
 Není možné použít rozhraní dědičnosti s vývoj s včasným kontrakt; To je konzistentní s způsob, jakým rozhraní chovat v jiné operace. Chcete-li použít rozhraní, které dědí základní rozhraní, použijte dva samostatné koncové body. První koncový bod používá zděděné kontrakt a druhý implementuje základní rozhraní.
