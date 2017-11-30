---
title: Verze serializace
ms.date: 08/08/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 90f2b1e73a24b0f732eaba4422faa9a1dcc15135
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="version-tolerant-serialization"></a>Verze serializace
Ve verzi 1.0 a 1.1 rozhraní .NET Framework byla problematický vytváření Serializovatelné typy, které by se znovu použít z jedné verze aplikace na další. V případě typu byl změněn přidáním pole navíc, by se objeví následující problémy:  
  
-   Starší verze aplikace by vyvolat výjimky dotaz k deserializaci nové verze původní typu.  
  
-   Novější verze aplikace by výjimku výjimky, při deserializaci starší verze typu s chybějící data.  
  
 Verze chybám serializace (VTS) je sada funkcí zavedena v rozhraní .NET Framework 2.0, který umožňuje snadněji v čase, chcete-li upravit Serializovatelné typy. Konkrétně jsou povoleny funkce VTS pro třídy, do kterého <xref:System.SerializableAttribute> byl použit atribut, včetně obecných typů. VTS umožňuje přidat nové pole do těchto tříd bez porušení kompatibilitu s jinými verzemi typu. Ukázkovou aplikaci, práce, najdete v části [verze odolný vůči chybám serializace technologie ukázka](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).  
  
 Jsou povoleny funkce VTS, používáte-li <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Navíc povoleny všechny funkce s výjimkou tolerance nadbytečná data také při použití <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Další informace o použití těchto tříd pro serializaci najdete v tématu [binární serializace](binary-serialization.md).  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>Seznam funkcí  
 Sada funkcí obsahuje následující položky:  
  
-   Odchylka nadbytečná nebo neočekávaná data. To umožňuje novější verze tohoto typu k odesílání dat ke starším verzím.  
  
-   Odchylka chybějících volitelnými daty. To umožňuje starší verze k odesílání dat do novější verze.  
  
-   Zpětná volání serializace. To umožňuje inteligentní výchozí nastavení hodnoty v případech, kdy je chybějící data.  
  
 Kromě toho je funkce k prohlášení, pokud byl přidán nový volitelné pole. Toto je <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> vlastnost <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu.  
  
 Tyto funkce jsou popsány podrobněji níže.  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a>Tolerance nadbytečné nebo neočekávané dat.  
 Všechna nadbytečná nebo neočekávaná data v minulosti během deserializace způsobeno výjimky, která je vyvolána. S VTS ve stejné situaci, všechna nadbytečná nebo neočekávaná data, je ignorován namísto způsobující výjimky, která je vyvolána. To umožňuje aplikacím, které používají novější verze tohoto typu (to znamená, že verzi, která obsahuje více polí) k odeslání informací do aplikace, které očekávají starších verzích stejného typu.  
  
 V následujícím příkladu doplňující data obsažená v `CountryField` verze 2.0 `Address` třída je ignorována, pokud starší aplikace deserializuje novější verzi.  
  
```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  
  
## <a name="tolerance-of-missing-data"></a>Tolerance chybějící data  
 Pole může být označen jako volitelné použitím <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu na ně. Během deserializace nepovinné údaje chybí, je-li pro Serializační stroj ignoruje absenci a nevyvolá výjimku. Aplikace, které očekávají starší verze typu tedy můžete odeslat data aplikací, které očekáváte novější verze stejného typu.  
  
 Následující příklad ukazuje, verze 2.0 `Address` třídy s `CountryField` pole označeno jako volitelné. Je-li starší aplikace odešle verze 1 a novější aplikace, která očekává verze 2.0, je ignorován neexistují data.  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
  
    [OptionalField]  
    public string CountryField;  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
  
    <OptionalField> _  
    Public CountryField As String  
End Class  
```  
  
## <a name="serialization-callbacks"></a>Zpětná volání serializace  
 Zpětná volání serializace jsou mechanismus, který poskytuje zachytávání do procesu serializaci nebo deserializaci na čtyři body.  
  
|Atribut|Když je volána metoda přidružené|Typické použití|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Před deserialization.*|Inicializuje výchozí hodnoty pro volitelná pole.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Po deserializace.|Opravte hodnoty volitelné pole založené na obsahu další pole.|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Před serializací.|Připravte pro serializaci. Můžete například vytvořte struktury volitelnými daty.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Po serializace.|Protokolovat události serializace.|  
  
 \*Tato zpětné volání je volána před konstruktor deserializace, pokud je k dispozici.  
  
### <a name="using-callbacks"></a>Pomocí zpětných volání  
 Chcete-li použít zpětná volání, vztahují na metodu, která přijme příslušný atribut <xref:System.Runtime.Serialization.StreamingContext> parametru. Pouze jednu metodu na třídu může být označena každý z těchto atributů. Příklad:  
  
```csharp  
[OnDeserializing]  
private void SetCountryRegionDefault(StreamingContext sc)  
{  
    CountryField = "Japan";  
}  
```  
  
```vb  
<OnDeserializing>  
Private Sub SetCountryRegionDefault(StreamingContext sc)  
    CountryField = "Japan";  
End Sub  
```  
  
 Tyto metody slouží pro správu verzí. Během deserializace volitelné pole nemusí být správně inicializován Pokud chybí data pro pole. Tento problém lze vyřešit tak, že vytvoření metody, která přiřadí správnou hodnotu, pak použití buď **OnDeserializingAttribute** nebo **OnDeserializedAttribute** atribut do metody.  
  
 Následující příklad ukazuje metodu v souvislosti s typem. Je-li starší verzi aplikace odešle instanci `Address` třídy na novější verzi aplikace, `CountryField` pole data budou chybějící. Ale po deserializace, bude pole nastavena na výchozí hodnotu "Japonsko."  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    [OptionalField]  
    public string CountryField;  
  
    [OnDeserializing]  
    private void SetCountryRegionDefault (StreamingContext sc)  
    {  
        CountryField = "Japan";  
    }  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    <OptionalField> _  
    Public CountryField As String  
  
    <OnDeserializing> _  
    Private Sub SetCountryRegionDefault(StreamingContext sc)  
        CountryField = "Japan";  
    End Sub  
End Class  
```  
  
## <a name="the-versionadded-property"></a>Vlastnost VersionAdded  
 **OptionalFieldAttribute** má **VersionAdded** vlastnost. V rozhraní .NET Framework verze 2.0 nepoužívá se. Je však potřeba zajistit, že typ bude kompatibilní s moduly budoucí serializace tuto vlastnost nastavit správně.  
  
 Vlastnost určuje, kterou verzi typu bylo přidáno daného pole. By měla být zvýšena podle právě jeden (počínaje 2) pokaždé, když je změněn na typ, jak je znázorněno v následujícím příkladu:  
  
```csharp  
// Version 1.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
}  
  
// Version 2.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded = 2)]  
    public string NickName;  
    [OptionalField(VersionAdded = 2)]  
    public DateTime BirthDate;  
}  
  
// Version 3.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded=2)]  
    public string NickName;  
    [OptionalField(VersionAdded=2)]  
    public DateTime BirthDate;  
  
    [OptionalField(VersionAdded=3)]  
    public int Weight;  
}  
```  
  
```vb  
' Version 1.0  
<Serializable> _  
Public Class Person  
    Public FullName  
End Class  
  
' Version 2.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
End Class  
  
' Version 3.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
  
    <OptionalField(VersionAdded := 3)> _  
    Public Weight As Integer  
End Class  
```  
  
## <a name="serializationbinder"></a>SerializationBinder  
 Někteří uživatelé muset které třídu k serializaci a deserializaci vzhledem k tomu, že u serverových a klientských je nutné zadat jinou verzi třídy ovládacího prvku. <xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třídu použít k řízení skutečné typy používané během serializace a deserializace.  Chcete-li použít tuto třídu, dosáhnout odvozením třídy od <xref:System.Runtime.Serialization.SerializationBinder> a přepište <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> a <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Řízení serializace a deserializace pomocí třídy SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).  
  
## <a name="best-practices"></a>Doporučené postupy  
 Chcete-li zajistit správnou verzí chování, postupujte podle těchto pravidel ke změně typu na verzi:  
  
-   Serializovaná pole nikdy odebrat.  
  
-   Nikdy použít <xref:System.NonSerializedAttribute> atributu na pole, pokud atribut nebyl použit na pole v předchozí verzi.  
  
-   Nikdy změnit název nebo typ serializovaného pole.  
  
-   Při přidávání nové serializovaných pole, použít **OptionalFieldAttribute** atribut.  
  
-   Při odebírání **NonSerializedAttribute** atribut z pole (který nebyl serializovatelný v předchozí verze), použijí **OptionalFieldAttribute** atribut.  
  
-   Pro všechny volitelná pole, nastavit smysluplný výchozí hodnoty použití zpětná volání serializace tolerantní 0 nebo **null** jako výchozí hodnoty jsou přijatelné.  
  
 Chcete-li zajistit, že budou kompatibilní s budoucí serializace moduly typu, postupujte podle následujících pokynů:  
  
-   Vždy nastaven **VersionAdded** vlastnost **OptionalFieldAttribute** atribut správně.  
  
-   Vyhněte se větvenou správy verzí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.SerializableAttribute>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 <xref:System.NonSerializedAttribute>  
 [Binární serializace](binary-serialization.md)
