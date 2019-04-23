---
title: Nástroj Contract-First
ms.date: 03/30/2017
ms.assetid: 0a880690-f460-4475-a5f4-9f91ce08fcc6
ms.openlocfilehash: ad0566eaff08d27e8368f091388adda7376a37ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978910"
---
# <a name="contract-first-tool"></a>Nástroj Contract-First
Kontrakty služeb často potřebují vytvořit z existujících služeb. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], třídy kontraktu dat může automaticky vytvořen z existující služby používat nástroj pro upřednostnění kontraktu. Pokud chcete použít nástroj pro upřednostnění kontraktu, musí být soubor definice schématu XML (XSD) stažen místně; Nástroj nemůže importovat kontrakty vzdálených dat přes protokol HTTP.

 Nástroj contract-first je integrována do sady Visual Studio 2012 jako úloha sestavení. Soubory kódu generovaných úkol sestavení se vytvoří pokaždé, když sestavení projektu tak, aby projekt můžete snadno přijmout změny v základní kontrakt služby.

 Schéma typů, které můžete importovat nástroj contract-first, patří:

```xml
<xsd:complexType>
<xsd:simpleType>
```

 Jednoduché typy nebude vytvořen, pokud jsou například primitiv `Int16` nebo `String`; komplexní typy nebudou generovány, pokud jsou typu `Collection`. Typy nebude vygenerováno také v případě, že jsou součástí jiného `xsd:complexType`. V těchto případech typy bude odkazovat na existující typy v projektu místo.

## <a name="adding-a-data-contract-to-a-project"></a>Přidání kontraktu dat do projektu
 Předtím, než je možné nástroj pro upřednostnění kontraktu, musí kontrakt služby (XSD) přidat do projektu. Pro účely tohoto přehledu se použije pro ilustraci stavící do funkce následující smlouvy. Tato definice služby je malou podmnožinu kontrakt služby používá rozhraní API Bingu pro vyhledávání.

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

 Chcete-li přidat výše kontraktu služby do projektu, klikněte pravým tlačítkem na projekt a vyberte **přidat nový...** . Vyberte definici schématu WCF podokně šablon dialogového okna a pojmenujte nový soubor SampleContract.xsd. Zkopírujte a vložte výše uvedený kód do zobrazení kódu nového souboru.

## <a name="configuring-contract-first-options"></a>Konfigurace možností upřednostnění kontraktu
 Možnosti kontraktem lze nastavit v nabídce vlastnosti projektu WCF. Chcete-li povolit rozvoje prvního kontraktu, vyberte **povolit XSD jako jazyk definice typu** zaškrtávací políčko na stránce WCF v okně Vlastnosti projektu.

 ![Snímek obrazovky s možností WCF pomocí rozvoje prvního kontraktu povolena.](./media/contract-first-tool/contract-first-options.png)

 Konfigurace rozšířených vlastností, klikněte na tlačítko Upřesnit.

 ![Nastavení generování kódu kontraktu dialogové okno Upřesnit.](./media/contract-first-tool/advanced-contract-settings.png)

 Toto nastavení lze nakonfigurovat pro generování kódu ze smluv. Nastavení se dá nakonfigurovat jenom pro všechny soubory v projektu. v tuto chvíli nelze konfigurovat pro jednotlivé soubory nastavení.

-   **Serializátor režimu**: Toto nastavení určuje, které serializátor se používá k přečtení soubory kontraktu služby. Když **serializátor XML** zaškrtnuto, **typy kolekcí** a **znovu použít typy** je zakázaná. Tyto možnosti platí pouze pro **serializátor kontraktu dat**.

-   **Znovu použít typy**: Toto nastavení určuje, které knihovny se používají pro znovuvyužití typů. Toto nastavení platí, pouze pokud **serializátor režimu** je nastavena na **serializátor kontraktu dat**.

-   **Typ kolekce**: Toto nastavení určuje plně kvalifikovaný nebo sestavením kvalifikovaný typ má být použit pro datový typ kolekce. Toto nastavení platí, pouze pokud **serializátor režimu** je nastavena na **serializátor kontraktu dat**.

-   **Typ slovníku**: Toto nastavení určuje plně kvalifikovaný nebo sestavením kvalifikovaný typ má být použit pro datový typ slovníku.

-   **EnableDataBinding**: Toto nastavení určuje, jestli se má implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní pro všechny datové typy pro implementaci datové vazby.

-   **Vyloučených typů**: Toto nastavení určuje seznam plně kvalifikovaný nebo sestavením kvalifikovaný typy, které se mají vyloučit z odkazovaných sestavení. Toto nastavení platí, pouze pokud **serializátor režimu** je nastavena na **serializátor kontraktu dat**.

-   **GenerateInternalTypes**: Toto nastavení určuje, jestli se mají generovat třídy, které jsou označeny jako vnitřní. Toto nastavení platí, pouze pokud **serializátor režimu** je nastavena na **serializátor kontraktu dat**.

-   **GenerateSerializableTypes**: Toto nastavení určuje, jestli se mají generovat třídy s <xref:System.SerializableAttribute> atribut. Toto nastavení platí, pouze pokud **serializátor režimu** je nastavena na **serializátor kontraktu dat**.

-   **ImportXMLTypes**: Toto nastavení určuje, jestli se má nakonfigurovat serializátor kontraktu dat. Chcete-li použít <xref:System.SerializableAttribute> atribut třídy bez <xref:System.Runtime.Serialization.DataContractAttribute> atribut.  Toto nastavení platí, pouze pokud **serializátor režimu** je nastavena na **serializátor kontraktu dat**.

-   **SupportFx35TypedDataSets**: Toto nastavení určuje, jestli se mají poskytnout dodatečné funkce pro typové datové sady vytvořené pro rozhraní .NET Framework 3.5. Když **serializátor režimu** je nastavena na **serializátor XML**, <xref:System.Data.Design.TypedDataSetSchemaImporterExtensionFx35> rozšíření se přidají do programu pro import schématu XML, když je tato hodnota nastavena na hodnotu True. Při **serializátor režimu** je nastavena na **serializátor kontraktu dat**, typ <xref:System.DateTimeOffset> budou vyloučeny z odkazů, pokud tato hodnota nastavena na hodnotu False, tak, aby <xref:System.DateTimeOffset> se vždy vygeneruje pro starší verze rozhraní framework.

-   **InputXsdFiles**: Toto nastavení určuje seznam vstupních souborů. Každý soubor musí obsahovat platné schéma XML.

-   **Jazyk**: Toto nastavení určuje jazyk kódu generovaného kontraktu. Nastavení musí být rozpoznat podle <xref:System.CodeDom.Compiler.CodeDomProvider>.

-   **NamespaceMappings**: Toto nastavení určuje mapování z cílové obory názvů XSD u oborů názvů CLR. Každé mapování by měl použijte následující formát:

    ```xml
    "<Schema Namespace>, <CLR Namespace>"
    ```

     Serializátor XML přijímá pouze jedno mapování v následujícím formátu:

    ```xml
    "*, <CLR Namespace>"
    ```

-   **OutputDirectory**: Toto nastavení určuje adresář, ve kterém se soubory kódu vygeneruje.

 Nastavení se použije ke generování typů kontraktu služby z kontraktu služby soubory při sestavení projektu.

## <a name="using-contract-first-development"></a>Pomocí rozvoje prvního kontraktu
 Po přidání kontraktu služby do projektu a potvrdíte nastavení sestavení, sestavte projekt stisknutím kombinace kláves **F6**. Typy definované v kontraktu služby pak bude k dispozici pro použití v projektu.

 Pokud chcete použít typy definované v kontraktu služby, přidejte odkaz na `ContractTypes` v aktuálním oboru názvů:

```csharp
using MyProjectNamespace.ContractTypes;
```

 Typy definované v kontraktu služby pak bude možné přeložit v projektu, jak je znázorněno níže:

 ![Třída SearchRequest zobrazení v IntelliSense po zadání prvních pár písmen.](./media/contract-first-tool/service-contract-types.png)

 Typy generované nástrojem jsou vytvořeny v souboru GeneratedXSDTypes.cs. Soubor je vytvořen \<adresáře projektu > /obj/\<konfiguraci sestavení > /XSDGeneratedCode/ adresáře ve výchozím nastavení. Ukázka schématu na začátku tohoto tématu je převést následujícím způsobem:

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
 Sestavování chyby a upozornění se zobrazí chyby a upozornění při parsování schématu XSD.

## <a name="interface-inheritance"></a>Dědičnost rozhraní
 Není možné použít dědičnost rozhraní s rozvoje prvního kontraktu; To je konzistentní se způsobem rozhraní chovají v jiných operacích. Pokud chcete používat rozhraní, které dědí základní rozhraní, použijte dva samostatné koncové body. První koncový bod používá zděděná smlouvy a druhý implementuje základní rozhraní.
