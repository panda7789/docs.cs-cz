---
title: "Vlastní serializace"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5718f19318121c2025b9d92a5947574289c1f4d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="custom-serialization"></a>Vlastní serializace
Vlastní serializace je proces řízení serializace a deserializace typu. Kontrolou serializace je možné zajistit kompatibilitu serializace, což je možnost k serializaci a deserializaci mezi verzemi typu, aniž by vás základní funkce služby typu. Například v první verzi typu, může existovat pouze dvě pole. V příští verzi typu jsou přidány několik více polí. Ještě druhý verze aplikace, musí mít k serializaci a deserializaci oba typy. Níže uvedené části popisují, jak řídit serializace.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  Ve verzích předchozí verze rozhraní .NET Framework 4.0 serializace dat vlastní uživatele v částečně důvěryhodné sestavení provést pomocí GetObjectData. Počínaje verzí 4.0, která metoda je označena <xref:System.Security.SecurityCriticalAttribute> atributů, což zabrání spouštění v částečně důvěryhodné sestavení. Chcete-li vyřešit tuto podmínku, implementovat <xref:System.Runtime.Serialization.ISafeSerializationData> rozhraní.  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>Spouštění vlastních metod během a po serializace  
 Doporučeným postupem a jednoduchý způsob, jak (zavedeno ve verzi 2.0 rozhraní .NET Framework) se mají být použity následující atributy metody, které se používají k odstranění dat během a po serializace:  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Tyto atributy umožňují typ k účasti v jedné z nebo všechny čtyři fází procesů serializace a deserializace. Atributy určují metody typu, který má být volána v každé fázi. Metody není přístup k datový proud serializace, ale místo toho bylo možné změnit objekt před a po serializaci, nebo před a po deserializace. Atributy lze použít na všech úrovních hierarchie dědičnosti typů a každá metoda je volána v hierarchii z základní k nejvíce odvozené. Tento mechanismus zabraňuje složitost a všechny výsledné problémy provádění <xref:System.Runtime.Serialization.ISerializable> rozhraní tím, že odpovědnost za serializace a deserializace za účelem implementace Většina odvozených. Kromě toho tento mechanismus umožňuje formátovací moduly, ignorovat naplnění polí a načtení z datový proud serializace. Podrobnosti a příklady řízení serializace a deserializace klikněte na tlačítko Předchozí odkazy.  
  
 Kromě toho při přidávání nového pole na existující serializovatelný typ., použije <xref:System.Runtime.Serialization.OptionalFieldAttribute> atributu na pole. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje absenci pole při zpracování datový proud, který chybí nové pole.  
  
## <a name="implementing-the-iserializable-interface"></a>Implementace rozhraní ISerializable  
 Druhý způsob k řízení serializace se dosahuje implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní na objekt. Upozorňujeme však, že metoda v předchozím oddílu nahrazuje tuto metodu za účelem serializace ovládacího prvku.  
  
 Kromě toho byste neměli používat výchozí serializace na třídu, která je označena [Serializable](xref:System.SerializableAttribute) atribut a má deklarativní nebo imperativní zabezpečení na úrovni třídy nebo na jeho konstruktory. Namísto toho měli vždy implementovat tyto třídy <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
 Implementace <xref:System.Runtime.Serialization.ISerializable> zahrnuje implementace `GetObjectData` metoda a speciální konstruktor, který se používá, pokud je objekt deserializován. Následující ukázkový kód ukazuje, jak implementovat <xref:System.Runtime.Serialization.ISerializable> na `MyObject` třídy z předchozího oddílu.  
  
```csharp  
[Serializable]  
public class MyObject : ISerializable   
{  
  public int n1;  
  public int n2;  
  public String str;  
  
  public MyObject()  
  {  
  }  
  
  protected MyObject(SerializationInfo info, StreamingContext context)  
  {  
    n1 = info.GetInt32("i");  
    n2 = info.GetInt32("j");  
    str = info.GetString("k");  
  }  
[SecurityPermissionAttribute(SecurityAction.Demand,   
SerializationFormatter =true)]  
  
public virtual void GetObjectData(SerializationInfo info, StreamingContext context)  
  {  
    info.AddValue("i", n1);  
    info.AddValue("j", n2);  
    info.AddValue("k", str);  
  }  
}  
```  
  
```vb  
<Serializable()>  _  
Public Class MyObject  
    Implements ISerializable  
    Public n1 As Integer  
    Public n2 As Integer  
    Public str As String  
  
    Public Sub New()   
    End Sub   
  
    Protected Sub New(ByVal info As SerializationInfo, _  
    ByVal context As StreamingContext)   
        n1 = info.GetInt32("i")  
        n2 = info.GetInt32("j")  
        str = info.GetString("k")  
    End Sub 'New  
  
    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Public Overridable Sub GetObjectData(ByVal info As _  
    SerializationInfo, ByVal context As StreamingContext)   
        info.AddValue("i", n1)  
        info.AddValue("j", n2)  
        info.AddValue("k", str)  
    End Sub   
End Class  
```  
  
 Když **GetObjectData** se nazývá během serializace, jste odpovědni za naplnění <xref:System.Runtime.Serialization.SerializationInfo> součástí volání metody. Přidáte proměnné mají být serializován jako dvojice název a hodnotu. Libovolný text, lze použít jako název. Máte svobodu rozhodnutí, které členské proměnné jsou přidány do <xref:System.Runtime.Serialization.SerializationInfo>, za předpokladu, že serializován dostatek dat. Chcete-li obnovit během deserializace objektu. Odvozené třídy by měly volat **GetObjectData** metody pro základní objekt Pokud pozdější implementuje <xref:System.Runtime.Serialization.ISerializable>.  
  
 Všimněte si, že serializace může povolit další kódu zobrazit nebo upravit data instance objektu, který je jinak nedostupný. Proto se vyžaduje kód, který provádí serializace [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) s <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> zadaného příznaku. Podle výchozích zásad Toto oprávnění nemá přístup k Internetu stáhnout nebo intranetu kód; Toto oprávnění je uděleno pouze kód v místním počítači. **GetObjectData** metoda musí být chráněny explicitně, buď pomocí náročných [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) s <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> příznak zadána nebo nástrojem náročných další oprávnění, které pomáhají konkrétně privátní data chránit.  
  
 Pokud pole private obsahuje citlivé informace, měli požadovat příslušná oprávnění na **GetObjectData** chránit data. Mějte na paměti, že kód, kterému byla udělena [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) s **SerializationFormatter** zadaného příznaku můžete zobrazit a upravit data uložená v privátním polím. Škodlivý volající udělena to [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) můžou zobrazovat data, jako je například umístění skrytý adresář nebo udělená oprávnění a data použít k zneužívají ohrožení zabezpečení v počítači. Úplný seznam příznaky oprávnění zabezpečení, můžete určit, najdete v článku [SecurityPermissionFlag výčtu](xref:System.Security.Permissions.SecurityPermissionFlag).  
  
 Je důležité, aby vystavila zátěži který po <xref:System.Runtime.Serialization.ISerializable> se přidá na třídu, musí implementovat obě **GetObjectData** a speciální konstruktoru. Kompilátor vás varuje, když **GetObjectData** chybí. Protože je nelze vynutit provádění konstruktor, bez upozornění je však k dispozici pokud chybí konstruktor a je vyvolána výjimka, pokud je proveden pokus o deserializaci třídy bez konstruktoru.  
  
 Aktuální návrh byl podporuje výše <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodu za účelem získání kolem potenciální problémy zabezpečení a správy verzí. Například `SetObjectData` metoda musí být veřejné, pokud je definována v rámci rozhraní; proto musí uživatelé napsat kód bránit proti nutnosti **SetObjectData** metodu volat vícekrát. Jinak se zlými úmysly aplikace, zavolá **SetObjectData** metoda objektu právě provádění operace může způsobit potenciální problémy.  
  
 Během deserializace <xref:System.Runtime.Serialization.SerializationInfo> je předán do třídy pomocí konstruktoru určených k tomuto účelu. Omezeními viditelnost umístí na konstruktoru jsou ignorovány, pokud je objekt deserializován; Třída tak můžete označit jako veřejné, chráněný, interní nebo privátní. Je však osvědčeným postupem zajistit konstruktoru chráněný, pokud zapečetěné třídy v takovém případě by měla být konstruktoru označena privátní. Konstruktor by měl také provést důkladné ověření vstupu. Chcete-li předejít zneužití škodlivým kódem, by měl konstruktoru vynutit stejné kontroly zabezpečení a oprávnění nutná k získání instance třídy pomocí jiných konstruktoru. Pokud není řídit tímto doporučením, škodlivý kód můžete preserialize objekt, získejte ovládacího prvku pomocí [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) s <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> příznak zadané a deserializaci objektu na klientském počítači obcházení žádné zabezpečení, které by byly použity během vytváření standardní instance pomocí veřejný konstruktor.  
  
 Chcete-li obnovit stav objektu, jednoduše načíst hodnoty proměnných z <xref:System.Runtime.Serialization.SerializationInfo> pomocí názvů používat během serializace. Pokud je základní třída implementuje <xref:System.Runtime.Serialization.ISerializable>, by měla být volána konstruktor základní třídy, aby umožnila základní objekt, který chcete obnovit své proměnné.  
  
 Pokud odvozujete od ten, který implementuje novou třídu <xref:System.Runtime.Serialization.ISerializable>, odvozené třídy musí implementovat obě konstruktoru a taky **GetObjectData** metoda, pokud má proměnné, které je potřeba serializovat. Následující příklad kódu ukazuje, jak to lze provést pomocí `MyObject` třídy, které jsou uvedeny dříve.  
  
```csharp  
[Serializable]  
public class ObjectTwo : MyObject  
{  
    public int num;  
  
    public ObjectTwo() : base()  
    {  
    }  
  
    protected ObjectTwo(SerializationInfo si,   
    StreamingContext context) : base(si,context)  
    {  
        num = si.GetInt32("num");  
    }  
[SecurityPermissionAttribute(SecurityAction.Demand,  
SerializationFormatter = true)]  
    public override void GetObjectData(SerializationInfo si,   
    StreamingContext context)  
    {  
        base.GetObjectData(si,context);  
        si.AddValue("num", num);  
    }  
}  
```  
  
```vb  
<Serializable()>  _  
Public Class ObjectTwo  
    Inherits MyObject  
    Public num As Integer  
  
    Public Sub New()   
  
    End Sub       
  
    Protected Sub New(ByVal si As SerializationInfo, _  
    ByVal context As StreamingContext)   
        MyBase.New(si, context)  
        num = si.GetInt32("num")      
    End Sub   
  
    <SecurityPermissionAttribute(SecurityAction.Demand, _  
    SerializationFormatter := True)>  _  
    Public Overrides Sub GetObjectData(ByVal si As _  
    SerializationInfo, ByVal context As StreamingContext)   
        MyBase.GetObjectData(si, context)  
        si.AddValue("num", num)      
    End Sub   
End Class  
```  
  
 Nezapomeňte volat základní třídy v konstruktor deserializace. Pokud to neuděláte, nikdy volání konstruktoru na základní třídy a objekt není úplně vytvořen po deserializaci.  
  
 Objekty jsou znovu vytvořena zevnitř a volání metod během deserializace může mít nežádoucí vedlejší účinky, protože volání metody může odkazovat na objekt odkazy, které nebyly byla deserializovat o dobu, kterou při volání. Pokud je třída deserializovat implementuje <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> metoda je volána automaticky, když byla zrušena její celý objekt grafu. V tomto okamžiku byly plně obnoveny všechny podřízené objekty odkazuje. Tabulka hash je typickým příkladem třídu, která je obtížné deserializaci bez použití naslouchací proces události. Vše je snadné k načtení dvojice klíč a hodnotu během deserializace, ale přidáním těchto objektů zpět do tabulky algoritmu hash může způsobit problémy vzhledem k tomu, že neexistuje žádná záruka této třídy, které odvozen z tabulky hash deserializovat. Volání metod z tabulky hash v této fázi není proto doporučuje.  
  
## <a name="see-also"></a>Viz také  
 [Binární serializace](binary-serialization.md)  
 [Serializace XML a SOAP](xml-and-soap-serialization.md)  
 [Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)
