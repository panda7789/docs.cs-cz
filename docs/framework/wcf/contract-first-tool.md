---
title: Nástroj Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: 36e1a3e19f802ca5b74cf50f5bcd57c167e31e33
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291707"
---
# <a name="contract-first-tool"></a>Nástroj Contract-First
Smlouvy o poskytování služeb je často nutné vytvořit ze stávajících služeb. V rozhraní .NET Framework 4.5 a novějších lze třídy kontraktů dat automaticky vytvořit z existujících služeb pomocí nástroje první smlouvy. Chcete-li použít nástroj pro vytvoření smlouvy, musí být soubor definice schématu XML (XSD) stažen místně; nástroj nemůže importovat smlouvy o vzdálených datech přes protokol HTTP.

 Nástroj první smlouvy je integrován do Sady Visual Studio 2012 jako úkol sestavení. Soubory kódu generované úlohou sestavení jsou vytvořeny při každém sestavení projektu, takže projekt může snadno přijmout změny v základní smlouvě o poskytování služeb.

 Typy schématu, které lze importovat nástroj první smlouvy patří následující:

```xml
<xsd:complexType>
 <xsd:simpleType>
 </xsd:simpleType>
</xsd:complexType>
```

 Jednoduché typy nebudou generovány, pokud jsou `Int16` primitivy, jako jsou nebo `String`; komplexní typy nebudou generovány, pokud `Collection`jsou typu . Typy také nebudou generovány, pokud jsou `xsd:complexType`součástí jiného . Ve všech těchto případech typy budou odkazovat na existující typy v projektu místo.

## <a name="adding-a-data-contract-to-a-project"></a>Přidání datové smlouvy do projektu
 Před použitím nástroje první smlouvy musí být do projektu přidána servisní smlouva (XSD). Pro účely tohoto přehledu bude následující smlouva použita k ilustraci funkcí na prvním místě smlouvy. Tato definice služby je malá podmnožina smlouvy o poskytování služeb používané rozhraní matná rozhraní API pro vyhledávání Bingu.

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

 Chcete-li do projektu přidat výše uvedenou servisní smlouvu, klepněte pravým tlačítkem myši na projekt a vyberte přidat **nový...**. Vyberte definici schématu v podokně WCF dialogového okna Šablony a pojmenujte nový soubor SampleContract.xsd. Zkopírujte a vložte výše uvedený kód do zobrazení kódu nového souboru.

## <a name="configuring-contract-first-options"></a>Konfigurace možností na prvním místě smlouvy
 Možnosti první smlouvy lze nakonfigurovat v nabídce Vlastnosti projektu WCF. Chcete-li povolit vývoj na prvním místě smlouvy, zaškrtněte políčko **Povolit XSD jako jazyk definice typu** na stránce WCF v okně vlastností projektu.

 ![Snímek obrazovky s možnostmi WCF s povoleným vývojem na prvním místě smlouvy.](./media/contract-first-tool/contract-first-options.png)

 Chcete-li konfigurovat upřesňující vlastnosti, klepněte na tlačítko Upřesnit.

 ![Dialogové okno Upřesnit nastavení generování kódu smlouvy.](./media/contract-first-tool/advanced-contract-settings.png)

 Následující upřesňující nastavení lze nakonfigurovat pro generování kódu ze smluv. Nastavení lze nakonfigurovat pouze pro všechny soubory v projektu; nastavení nelze v tuto chvíli nakonfigurovat pro jednotlivé soubory.

- **Serializační režim**: Toto nastavení určuje, který serializátor se používá pro čtení souborů servisní smlouvy. Pokud je vybrán **serializátor XML,** jsou zakázány možnosti **Typy kolekcí** a **Typy opakovaného použití.** Tyto možnosti platí pouze pro **serializátor smlouvy dat**.

- **Znovu použít typy**: Toto nastavení určuje, které knihovny se používají pro opakované použití typu. Toto nastavení platí pouze v případě, že je **režim serializátoru** nastaven na **serializátor smlouvy s daty**.

- **Typ kolekce**: Toto nastavení určuje plně kvalifikovaný typ nebo typ s kvalifikací sestavení, který má být použit pro datový typ kolekce. Toto nastavení platí pouze v případě, že je **režim serializátoru** nastaven na **serializátor smlouvy s daty**.

- **Typ slovníku**: Toto nastavení určuje plně kvalifikovaný typ nebo typ s kvalifikací sestavení, který se má použít pro datový typ slovníku.

- **EnableDataBinding**: Toto nastavení určuje, zda má být implementováno <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní na všech datových typech k implementaci datové vazby.

- **ExcludedTypes**:Toto nastavení určuje seznam plně kvalifikovaných typů nebo typů kvalifikovaných pro sestavení, které mají být vyloučeny z odkazovaných sestav. Toto nastavení platí pouze v případě, že je **režim serializátoru** nastaven na **serializátor smlouvy s daty**.

- **GenerateInternalTypes**: Toto nastavení určuje, zda mají být generovány třídy, které jsou označeny jako interní. Toto nastavení platí pouze v případě, že je **režim serializátoru** nastaven na **serializátor smlouvy s daty**.

- **GenerateSerializableTypes**: Toto nastavení určuje, <xref:System.SerializableAttribute> zda se mají generovat třídy s atributem. Toto nastavení platí pouze v případě, že je **režim serializátoru** nastaven na **serializátor smlouvy s daty**.

- **ImportXMLTypes**: Toto nastavení určuje, zda má být <xref:System.SerializableAttribute> nakonfigurován serializátor datové smlouvy tak, aby atribut použil na třídy bez atributu. <xref:System.Runtime.Serialization.DataContractAttribute>  Toto nastavení platí pouze v případě, že je **režim serializátoru** nastaven na **serializátor smlouvy s daty**.

- **SupportFx35TypedDataSets**: Toto nastavení určuje, zda má být poskytnuta další funkce pro zadané datové sady vytvořené pro rozhraní .NET Framework 3.5. Pokud je **režim serializátoru** <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> nastaven na **serializátor XML**, bude rozšíření přidáno do importu schématu XML, pokud je tato hodnota nastavena na hodnotu True. Pokud **serializační režim** je nastavena na <xref:System.DateTimeOffset> **serializátor smlouvy dat**, typ bude vyloučen z <xref:System.DateTimeOffset> odkazy, pokud je tato hodnota nastavena na False, tak, aby a je vždy generována pro starší verze architektury.

- **InputXsdFiles**: Toto nastavení určuje seznam vstupních souborů. Každý soubor musí obsahovat platné schéma XML.

- **Jazyk**: Toto nastavení určuje jazyk generovaného kódu smlouvy. Nastavení musí být rozpoznatelné podle <xref:System.CodeDom.Compiler.CodeDomProvider>.

- **NamespaceMappings**: Toto nastavení určuje mapování z cílových oborů názvů XSD na obory názvů CLR. Každé mapování by mělo používat následující formát:

    ```xml
    "Schema Namespace, CLR Namespace"
    ```

     Serializátor XML přijímá pouze jedno mapování v následujícím formátu:

    ```xml
    "*, CLR Namespace"
    ```

- **OutputDirectory**: Toto nastavení určuje adresář, ve kterém budou generovány soubory kódu.

 Nastavení bude použito ke generování typů servisních smluv ze souborů servisní smlouvy při vytváření projektu.

## <a name="using-contract-first-development"></a>Použití vývoje na prvním místě smlouvy
 Po přidání smlouvy o poskytování služeb do projektu a potvrzení nastavení sestavení vytvořte projekt stisknutím **klávesy F6**. Typy definované ve smlouvě o poskytování služeb pak budou k dispozici pro použití v projektu.

 Chcete-li použít typy definované ve smlouvě `ContractTypes` o poskytování služeb, přidejte odkaz pod aktuální obor názvů:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Typy definované v servisní smlouvě pak budou v projektu řešitelné, jak je znázorněno níže:

 ![SearchRequest třída zobrazena v IntelliSense po zadání prvních několik písmen.](./media/contract-first-tool/service-contract-types.png)

 Typy generované nástrojem jsou vytvořeny v souboru GeneratedXSDTypes.cs. Soubor je vytvořen \<v adresáři projektu\<>/obj/ konfigurace sestavení>/XSDGeneratedCode/ adresáře ve výchozím nastavení. Ukázkové schéma na začátku tohoto článku je převedeno takto:

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

## <a name="errors-and-warnings"></a>Chyby a varování
 Chyby a upozornění při analýzách schématu XSD se zobrazí jako chyby sestavení a upozornění.

## <a name="interface-inheritance"></a>Dědičnost rozhraní
 Není možné použít dědičnost rozhraní s vývojem první smlouvy; To je v souladu se způsobem, jakým se rozhraní chovají v jiných operacích. Chcete-li použít rozhraní, které dědí základní rozhraní, použijte dva samostatné koncové body. První koncový bod používá zděděnou smlouvu a druhý koncový bod implementuje základní rozhraní.
