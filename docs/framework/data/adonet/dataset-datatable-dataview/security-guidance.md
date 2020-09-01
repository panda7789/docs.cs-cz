---
title: Doprovodné materiály k zabezpečení datových sad a DataTable
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 4fe8a062c762cc70d33243e3443aa9bf55635f98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137614"
---
# <a name="dataset-and-datatable-security-guidance"></a><span data-ttu-id="38e71-102">Doprovodné materiály k zabezpečení datových sad a DataTable</span><span class="sxs-lookup"><span data-stu-id="38e71-102">DataSet and DataTable security guidance</span></span>

<span data-ttu-id="38e71-103">Tento článek se týká:</span><span class="sxs-lookup"><span data-stu-id="38e71-103">This article applies to:</span></span>

* <span data-ttu-id="38e71-104">.NET Framework (všechny verze)</span><span class="sxs-lookup"><span data-stu-id="38e71-104">.NET Framework (all versions)</span></span>
* <span data-ttu-id="38e71-105">.NET Core a novější</span><span class="sxs-lookup"><span data-stu-id="38e71-105">.NET Core and later</span></span>
* <span data-ttu-id="38e71-106">.NET 5,0 a novější</span><span class="sxs-lookup"><span data-stu-id="38e71-106">.NET 5.0 and later</span></span>

<span data-ttu-id="38e71-107">Typy [DataSet](/dotnet/api/system.data.dataset) a [DataTable](/dotnet/api/system.data.datatable) jsou starší komponenty rozhraní .NET, které umožňují reprezentace datových sad jako spravovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="38e71-107">The [DataSet](/dotnet/api/system.data.dataset) and [DataTable](/dotnet/api/system.data.datatable) types are legacy .NET components that allow representing data sets as managed objects.</span></span> <span data-ttu-id="38e71-108">Tyto součásti byly představeny v rozhraní .NET 1,0 jako součást původní [infrastruktury ADO.NET](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span><span class="sxs-lookup"><span data-stu-id="38e71-108">These components were introduced in .NET 1.0 as part of the original [ADO.NET infrastructure](/dotnet/framework/data/adonet/dataset-datatable-dataview/).</span></span> <span data-ttu-id="38e71-109">Jejich cílem bylo poskytnout spravované zobrazení přes relační datovou sadu, a vyříznout si tak, jestli základní zdroj dat byl XML, SQL nebo jiná technologie.</span><span class="sxs-lookup"><span data-stu-id="38e71-109">Their goal was to provide a managed view over a relational data set, abstracting away whether the underlying source of the data was XML, SQL, or another technology.</span></span>

<span data-ttu-id="38e71-110">Další informace o ADO.NET, včetně pokročilejších paradigmat zobrazení dat, najdete v [dokumentaci k ADO.NET](/dotnet/framework/data/adonet/).</span><span class="sxs-lookup"><span data-stu-id="38e71-110">For more information on ADO.NET, including more modern data view paradigms, see [the ADO.NET documentation](/dotnet/framework/data/adonet/).</span></span>

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a><span data-ttu-id="38e71-111">Výchozí omezení při deserializaci datové sady nebo DataTable z XML</span><span class="sxs-lookup"><span data-stu-id="38e71-111">Default restrictions when deserializing a DataSet or DataTable from XML</span></span>

<span data-ttu-id="38e71-112">Na všech podporovaných verzích .NET Framework, .NET Core a .NET `DataSet` a `DataTable` umístěte následující omezení pro typy objektů, které mohou být k dispozici v deserializovaných datech.</span><span class="sxs-lookup"><span data-stu-id="38e71-112">On all supported versions of .NET Framework, .NET Core, and .NET, `DataSet` and `DataTable` place the following restrictions on what types of objects may be present in the deserialized data.</span></span> <span data-ttu-id="38e71-113">Ve výchozím nastavení je tento seznam omezen na:</span><span class="sxs-lookup"><span data-stu-id="38e71-113">By default, this list is restricted to:</span></span>

* <span data-ttu-id="38e71-114">Primitivní a primitivní ekvivalenty: `bool` ,,,, `char` `sbyte` `byte` `short` , `ushort` , `int` , `uint` , `long` ,,,, `ulong` `float` `double` `decimal` `DateTime` `DateTimeOffset` `TimeSpan` `string` `Guid` `SqlBinary` `SqlBoolean` `SqlByte` `SqlBytes` `SqlChars` `SqlDateTime` `SqlDecimal` `SqlDouble` `SqlGuid` `SqlInt16` `SqlInt32` `SqlInt64` `SqlMoney` `SqlSingle` `SqlString` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, a.</span><span class="sxs-lookup"><span data-stu-id="38e71-114">Primitives and primitive equivalents: `bool`, `char`, `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, `decimal`, `DateTime`, `DateTimeOffset`, `TimeSpan`, `string`, `Guid`, `SqlBinary`, `SqlBoolean`, `SqlByte`, `SqlBytes`, `SqlChars`, `SqlDateTime`, `SqlDecimal`, `SqlDouble`, `SqlGuid`, `SqlInt16`, `SqlInt32`, `SqlInt64`, `SqlMoney`, `SqlSingle`, and `SqlString`.</span></span>
* <span data-ttu-id="38e71-115">Běžně používané neprimitivní prvky: `Type` , a `Uri` `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="38e71-115">Commonly used non-primitives: `Type`, `Uri`, and `BigInteger`.</span></span>
* <span data-ttu-id="38e71-116">Běžně používané typy _System. Drawing_ : `Color` , `Point` , `PointF` , `Rectangle` , `RectangleF` , a `Size` `SizeF` .</span><span class="sxs-lookup"><span data-stu-id="38e71-116">Commonly used _System.Drawing_ types: `Color`, `Point`, `PointF`, `Rectangle`, `RectangleF`, `Size`, and `SizeF`.</span></span>
* <span data-ttu-id="38e71-117">`Enum` druhy.</span><span class="sxs-lookup"><span data-stu-id="38e71-117">`Enum` types.</span></span>
* <span data-ttu-id="38e71-118">Pole a seznamy výše uvedených typů.</span><span class="sxs-lookup"><span data-stu-id="38e71-118">Arrays and lists of the above types.</span></span>

<span data-ttu-id="38e71-119">Pokud příchozí XML data obsahují objekt, jehož typ není v tomto seznamu:</span><span class="sxs-lookup"><span data-stu-id="38e71-119">If the incoming XML data contains an object whose type is not in this list:</span></span>

* <span data-ttu-id="38e71-120">V následující zprávě a trasování zásobníku je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="38e71-120">An exception is thrown with the following message and stack trace.</span></span>  
<span data-ttu-id="38e71-121">Chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="38e71-121">Error Message:</span></span>  
<span data-ttu-id="38e71-122">System. InvalidOperationException: type \<Type Name\> , Version = \<n.n.n.n\> , Culture = \<culture\> , PublicKeyToken = není \<token value\> tady povolený.</span><span class="sxs-lookup"><span data-stu-id="38e71-122">System.InvalidOperationException : Type '\<Type Name\>, Version=\<n.n.n.n\>, Culture=\<culture\>, PublicKeyToken=\<token value\>' is not allowed here.</span></span> <span data-ttu-id="38e71-123">Další podrobnosti najdete v tématu [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) .</span><span class="sxs-lookup"><span data-stu-id="38e71-123">See [https://go.microsoft.com/fwlink/?linkid=2132227](https://go.microsoft.com/fwlink/?linkid=2132227) for more details.</span></span>  
<span data-ttu-id="38e71-124">Trasování zásobníku:</span><span class="sxs-lookup"><span data-stu-id="38e71-124">Stack Trace:</span></span>  
<span data-ttu-id="38e71-125">v System. data. TypeLimiter. EnsureTypeIsAllowed (typ typu, TypeLimiter capturedLimiter)</span><span class="sxs-lookup"><span data-stu-id="38e71-125">at System.Data.TypeLimiter.EnsureTypeIsAllowed(Type type, TypeLimiter capturedLimiter)</span></span>  
<span data-ttu-id="38e71-126">v System. data. DataColumn. UpdateColumnType (typ typu, StorageType typeCode)</span><span class="sxs-lookup"><span data-stu-id="38e71-126">at System.Data.DataColumn.UpdateColumnType(Type type, StorageType typeCode)</span></span>  
<span data-ttu-id="38e71-127">v System. data. DataColumn. set_DataType (hodnota typu)</span><span class="sxs-lookup"><span data-stu-id="38e71-127">at System.Data.DataColumn.set_DataType(Type value)</span></span>  

* <span data-ttu-id="38e71-128">Operace deserializace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="38e71-128">The deserialization operation fails.</span></span>

<span data-ttu-id="38e71-129">Při načítání kódu XML do existující `DataSet` `DataTable` instance nebo je také nutné vzít v úvahu existující definice sloupců.</span><span class="sxs-lookup"><span data-stu-id="38e71-129">When loading XML into an existing `DataSet` or `DataTable` instance, the existing column definitions are also taken into account.</span></span> <span data-ttu-id="38e71-130">Pokud tabulka již obsahuje definici sloupce vlastního typu, tento typ je dočasně přidán do seznamu povolených po dobu trvání operace deserializace XML.</span><span class="sxs-lookup"><span data-stu-id="38e71-130">If the table already contains a column definition of a custom type, that type is temporarily added to the allow list for the duration of the XML deserialization operation.</span></span>

> [!NOTE]
> <span data-ttu-id="38e71-131">Po přidání sloupců do nástroje nebude `DataTable` `ReadXml` ze souboru XML Přečtěte schéma a pokud se schéma neshoduje, nebude se v záznamech číst, takže budete muset přidat všechny sloupce sami, abyste mohli tuto metodu použít.</span><span class="sxs-lookup"><span data-stu-id="38e71-131">Once you add columns to a `DataTable`, `ReadXml` will not read the schema from the XML, and if the schema does not match it will also not read in the records, so you will need to add all the columns yourself to use this method.</span></span>

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

<span data-ttu-id="38e71-132">Omezení typu objektu platí také při použití `XmlSerializer` k deserializaci instance `DataSet` nebo `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="38e71-132">The object type restrictions also apply when using `XmlSerializer` to deserialize an instance of `DataSet` or `DataTable`.</span></span> <span data-ttu-id="38e71-133">Nemusí však platit při použití `BinaryFormatter` k deserializaci instance `DataSet` nebo `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="38e71-133">However, they may not apply when using `BinaryFormatter` to deserialize an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="38e71-134">Omezení typu objektu neplatí při použití `DataAdapter.Fill` , například pokud `DataTable` je instance naplněna přímo z databáze bez použití rozhraní API deserializace XML.</span><span class="sxs-lookup"><span data-stu-id="38e71-134">The object type restrictions don't apply when using `DataAdapter.Fill`, such as when a `DataTable` instance is populated directly from a database without using the XML deserialization APIs.</span></span>

### <a name="extend-the-list-of-allowed-types"></a><span data-ttu-id="38e71-135">Rozšíří seznam povolených typů.</span><span class="sxs-lookup"><span data-stu-id="38e71-135">Extend the list of allowed types</span></span>

<span data-ttu-id="38e71-136">Aplikace může rozšířit seznam povolených typů tak, aby kromě předdefinovaných typů uvedených výše zahrnoval vlastní typy.</span><span class="sxs-lookup"><span data-stu-id="38e71-136">An app can extend the allowed types list to include custom types in addition to the built-in types listed above.</span></span> <span data-ttu-id="38e71-137">Pokud se seznam povolených typů rozšíří, ovlivní tato změna _všechny_ `DataSet` `DataTable` instance a v rámci aplikace.</span><span class="sxs-lookup"><span data-stu-id="38e71-137">If extending the allowed types list, the change affects _all_ `DataSet` and `DataTable` instances within the app.</span></span> <span data-ttu-id="38e71-138">Typy nelze odebrat z předdefinovaných povolených typů.</span><span class="sxs-lookup"><span data-stu-id="38e71-138">Types cannot be removed from the built-in allowed types list.</span></span>

#### <a name="extend-through-configuration-net-framework-40---48"></a><span data-ttu-id="38e71-139">Rozšířené konfigurace (.NET Framework 4,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="38e71-139">Extend through configuration (.NET Framework 4.0 - 4.8)</span></span>

<span data-ttu-id="38e71-140">_App.config_ lze použít k roztažení seznamu povolených typů.</span><span class="sxs-lookup"><span data-stu-id="38e71-140">_App.config_ can be used to extend the allowed types list.</span></span> <span data-ttu-id="38e71-141">Chcete-li roztáhnout seznam povolených typů:</span><span class="sxs-lookup"><span data-stu-id="38e71-141">To extend the allowed types list:</span></span>

* <span data-ttu-id="38e71-142">Pomocí `<configSections>` elementu přidejte odkaz na oddíl _System. data_ Configuration.</span><span class="sxs-lookup"><span data-stu-id="38e71-142">Use the `<configSections>` element to add a reference to the _System.Data_ configuration section.</span></span>
* <span data-ttu-id="38e71-143">Použijte `<system.data.dataset.serialization>` / `<allowedTypes>` k určení dalších typů.</span><span class="sxs-lookup"><span data-stu-id="38e71-143">Use `<system.data.dataset.serialization>`/`<allowedTypes>` to specify additional types.</span></span>

<span data-ttu-id="38e71-144">Každý `<add>` prvek musí určovat pouze jeden typ pomocí kvalifikovaného názvu typu sestavení.</span><span class="sxs-lookup"><span data-stu-id="38e71-144">Each `<add>` element must specify only one type by using its assembly qualified type name.</span></span> <span data-ttu-id="38e71-145">Chcete-li přidat další typy do seznamu povolených typů, použijte více `<add>` prvků.</span><span class="sxs-lookup"><span data-stu-id="38e71-145">To add additional types to the allowed types list, use multiple `<add>` elements.</span></span>

<span data-ttu-id="38e71-146">Následující příklad ukazuje rozšíření seznamu povolených typů přidáním vlastního typu `Fabrikam.CustomType` .</span><span class="sxs-lookup"><span data-stu-id="38e71-146">The following sample shows extending the allowed types list by adding the custom type `Fabrikam.CustomType`.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="38e71-147">Chcete-li načíst kvalifikovaný název sestavení typu, použijte vlastnost [Type. AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-147">To retrieve the assembly qualified name of a type, use the [Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) property, as demonstrated in the following code.</span></span>

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a><span data-ttu-id="38e71-148">Rozšířené konfigurace (.NET Framework 2,0-3,5)</span><span class="sxs-lookup"><span data-stu-id="38e71-148">Extend through configuration (.NET Framework 2.0 - 3.5)</span></span>

<span data-ttu-id="38e71-149">Pokud se vaše aplikace zaměřuje .NET Framework 2,0 nebo 3,5, můžete k roztažení seznamu povolených typů dál použít výše uvedený _App.config_ mechanismus.</span><span class="sxs-lookup"><span data-stu-id="38e71-149">If your app targets .NET Framework 2.0 or 3.5, you can still use the above _App.config_ mechanism to extend the allowed types list.</span></span> <span data-ttu-id="38e71-150">Váš element však `<configSections>` bude vypadat mírně odlišně, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="38e71-150">However, your `<configSections>` element will look slightly different, as shown in the following code:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a><span data-ttu-id="38e71-151">Roztažení programově (.NET Framework, .NET Core, .NET 5.0 +)</span><span class="sxs-lookup"><span data-stu-id="38e71-151">Extend programmatically (.NET Framework, .NET Core, .NET 5.0+)</span></span>

<span data-ttu-id="38e71-152">Seznam povolených typů lze také programově rozšířit pomocí [AppDomain. SetData](/dotnet/api/system.appdomain.setdata) s dobře známým klíčem _System. data. DataSetDefaultAllowedTypes_, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-152">The list of allowed types can also be extended programmatically by using [AppDomain.SetData](/dotnet/api/system.appdomain.setdata) with the well-known key _System.Data.DataSetDefaultAllowedTypes_, as shown in the following code.</span></span>

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

<span data-ttu-id="38e71-153">Při použití mechanismu rozšíření musí být hodnota přidružená k klíči _System. data. DataSetDefaultAllowedTypes_ typu `Type[]` .</span><span class="sxs-lookup"><span data-stu-id="38e71-153">If using the extension mechanism, the value associated with the key _System.Data.DataSetDefaultAllowedTypes_ must be of type `Type[]`.</span></span>

<span data-ttu-id="38e71-154">V .NET Framework lze seznam povolených typů rozšířit pomocí _App.config_ a `AppDomain.SetData` .</span><span class="sxs-lookup"><span data-stu-id="38e71-154">On .NET Framework, the list of allowed types may be extended both with _App.config_ and `AppDomain.SetData`.</span></span> <span data-ttu-id="38e71-155">V tomto případě `DataSet` a `DataTable` povolí, aby objekt byl rekonstruován jako součást dat, pokud je jeho typ přítomen v obou seznamech.</span><span class="sxs-lookup"><span data-stu-id="38e71-155">In this case, `DataSet` and `DataTable` will allow an object to be deserialized as part of the data if its type is present in either list.</span></span>

### <a name="run-an-app-in-audit-mode-net-framework"></a><span data-ttu-id="38e71-156">Spuštění aplikace v režimu auditování (.NET Framework)</span><span class="sxs-lookup"><span data-stu-id="38e71-156">Run an app in audit mode (.NET Framework)</span></span>

<span data-ttu-id="38e71-157">V .NET Framework `DataSet` a `DataTable` Poskytněte možnost režimu auditování.</span><span class="sxs-lookup"><span data-stu-id="38e71-157">In .NET Framework, `DataSet` and `DataTable` provide an audit mode capability.</span></span> <span data-ttu-id="38e71-158">Když je povolen režim auditování `DataSet` a `DataTable` porovná typy příchozích objektů se seznamem povolených typů.</span><span class="sxs-lookup"><span data-stu-id="38e71-158">When audit mode is enabled, `DataSet` and `DataTable` compare the types of incoming objects against the allowed types list.</span></span> <span data-ttu-id="38e71-159">Nicméně pokud objekt, jehož typ není povolen, **není vyvolána výjimka** .</span><span class="sxs-lookup"><span data-stu-id="38e71-159">However, if an object whose type is not allowed is seen, an exception is **not** thrown.</span></span> <span data-ttu-id="38e71-160">Místo toho `DataSet` a `DataTable` upozorněte všechny připojené `TraceListener` instance, které jsou k dispozici podezřelý typ, což umožňuje `TraceListener` Protokolovat tyto informace.</span><span class="sxs-lookup"><span data-stu-id="38e71-160">Instead, `DataSet` and `DataTable` notify any attached `TraceListener` instances that a suspicious type is present, allowing the `TraceListener` to log this information.</span></span> <span data-ttu-id="38e71-161">Není vyvolána žádná výjimka a operace deserializace pokračuje.</span><span class="sxs-lookup"><span data-stu-id="38e71-161">No exception is thrown and the deserialization operation continues.</span></span>

> [!WARNING]
> <span data-ttu-id="38e71-162">Spuštění aplikace v režimu auditu by mělo být jenom dočasnou mírou, která se používá pro testování.</span><span class="sxs-lookup"><span data-stu-id="38e71-162">Running an app in "audit mode" should only be a temporary measure used for testing.</span></span> <span data-ttu-id="38e71-163">Když je povolen režim auditu `DataSet` a `DataTable` nevynutila se omezení typů, která můžou do aplikace zavádět bezpečnostní otvor.</span><span class="sxs-lookup"><span data-stu-id="38e71-163">When audit mode is enabled, `DataSet` and `DataTable` do not enforce type restrictions, which can introduce a security hole inside your app.</span></span> <span data-ttu-id="38e71-164">Další informace najdete v oddílech s názvem [Odebrání všech omezení typu](#ratr) a [bezpečnosti s ohledem na nedůvěryhodný vstup](#swr).</span><span class="sxs-lookup"><span data-stu-id="38e71-164">For more information, see the sections titled [Removing all type restrictions](#ratr) and [Safety with regard to untrusted input](#swr).</span></span>

<span data-ttu-id="38e71-165">Režim auditování lze povolit prostřednictvím _App.config_:</span><span class="sxs-lookup"><span data-stu-id="38e71-165">Audit mode can be enabled through _App.config_:</span></span>

* <span data-ttu-id="38e71-166">Informace o správné hodnotě pro vložení elementu najdete v části [rozšíření prostřednictvím konfiguračního](#etc) souboru v tomto dokumentu `<configSections>` .</span><span class="sxs-lookup"><span data-stu-id="38e71-166">See the [Extending through configuration](#etc) section in this document for information on the proper value to put for the `<configSections>` element.</span></span>
* <span data-ttu-id="38e71-167">Použijte `<allowedTypes auditOnly="true">` k povolení režimu auditování, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-167">Use `<allowedTypes auditOnly="true">` to enable audit mode, as shown in the following markup.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

<span data-ttu-id="38e71-168">Po povolení režimu auditu můžete použít _App.config_ pro připojení k `TraceListener` `DataSet` předdefinovanému `TraceSource.` názvu integrovaného zdroje trasování je _System. data. DataSet_.</span><span class="sxs-lookup"><span data-stu-id="38e71-168">Once audit mode is enabled, you can use _App.config_ to connect your preferred `TraceListener` to the `DataSet` built-in `TraceSource.` The name of the built-in trace source is _System.Data.DataSet_.</span></span> <span data-ttu-id="38e71-169">Následující příklad ukazuje zápis událostí trasování do konzoly nástroje _a_ do souboru protokolu na disku.</span><span class="sxs-lookup"><span data-stu-id="38e71-169">The following sample demonstrates writing trace events to the console _and_ to a log file on disk.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

<span data-ttu-id="38e71-170">Další informace o `TraceSource` a `TraceListener` najdete v dokumentu [Postupy: použití TraceSource a filtrů s naslouchacími procesy trasování](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="38e71-170">For more information on `TraceSource` and `TraceListener`, see the document [How to: Use TraceSource and Filters with Trace Listeners](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span>

> [!NOTE]
> <span data-ttu-id="38e71-171">Spuštění aplikace v režimu auditování není v rozhraní .NET Core nebo .NET 5,0 a novějších k dispozici.</span><span class="sxs-lookup"><span data-stu-id="38e71-171">Running an app in audit mode is not available in .NET Core or in .NET 5.0 and later.</span></span>

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a><span data-ttu-id="38e71-172">Odebrat všechna omezení typů</span><span class="sxs-lookup"><span data-stu-id="38e71-172">Remove all type restrictions</span></span>

<span data-ttu-id="38e71-173">Pokud aplikace musí odebrat všechny omezující omezení typu `DataSet` a `DataTable` :</span><span class="sxs-lookup"><span data-stu-id="38e71-173">If an app must remove all type limiting restrictions from `DataSet` and `DataTable`:</span></span>

* <span data-ttu-id="38e71-174">Existuje několik možností, jak potlačit omezení typu omezení.</span><span class="sxs-lookup"><span data-stu-id="38e71-174">There are several options to suppress type limiting restrictions.</span></span>
* <span data-ttu-id="38e71-175">Dostupné možnosti závisí na architektuře, na kterou aplikace cílí.</span><span class="sxs-lookup"><span data-stu-id="38e71-175">The options available depend on the framework the app targets.</span></span>

> [!WARNING]
> <span data-ttu-id="38e71-176">Odebrání všech omezení typu může do aplikace zavádět bezpečnostní otvor.</span><span class="sxs-lookup"><span data-stu-id="38e71-176">Removing all type restrictions can introduce a security hole inside the app.</span></span> <span data-ttu-id="38e71-177">Při použití tohoto mechanismu ověřte, že aplikace **nepoužívá** `DataSet` nebo `DataTable` čte nedůvěryhodný vstup.</span><span class="sxs-lookup"><span data-stu-id="38e71-177">When using this mechanism, ensure the app does **not** use `DataSet` or `DataTable` to read untrusted input.</span></span> <span data-ttu-id="38e71-178">Další informace najdete v článku [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) a v následující části [s názvem bezpečnost s ohledem na nedůvěryhodný vstup](#swr).</span><span class="sxs-lookup"><span data-stu-id="38e71-178">For more information, see [CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) and the following section titled [Safety with regard to untrusted input](#swr).</span></span>

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a><span data-ttu-id="38e71-179">Prostřednictvím konfigurace AppContext (.NET Framework 4,6-4,8, .NET Core 2,1 a novější, .NET 5,0 a novější)</span><span class="sxs-lookup"><span data-stu-id="38e71-179">Through AppContext configuration (.NET Framework 4.6 - 4.8, .NET Core 2.1 and later, .NET 5.0 and later)</span></span>

<span data-ttu-id="38e71-180">`AppContext`Přepínač, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` , pokud je nastaveno na `true` Odebrat všechny omezující omezení typu z `DataSet` a `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="38e71-180">The `AppContext` switch, `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation`, when set to `true` removes all type limiting restrictions from `DataSet` and `DataTable`.</span></span>

<span data-ttu-id="38e71-181">V .NET Framework lze tento přepínač Povolit prostřednictvím _App.config_, jak je znázorněno v následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="38e71-181">In .NET Framework, this switch can be enabled via _App.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

<span data-ttu-id="38e71-182">V ASP.NET není `<AppContextSwitchOverrides>` element k dispozici.</span><span class="sxs-lookup"><span data-stu-id="38e71-182">In ASP.NET, the `<AppContextSwitchOverrides>` element is not available.</span></span> <span data-ttu-id="38e71-183">Místo toho lze přepínač Povolit prostřednictvím _Web.config_, jak je znázorněno v následující konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="38e71-183">Instead, the switch can be enabled via _Web.config_, as shown in the following configuration:</span></span>

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="38e71-184">Další informace naleznete v tématu [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="38e71-184">For more information, see the [\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element.</span></span>

<span data-ttu-id="38e71-185">V rozhraní .NET Core, .NET 5 a ASP.NET Core toto nastavení ovládá _runtimeconfig.jsna_, jak je znázorněno v následujícím kódu JSON:</span><span class="sxs-lookup"><span data-stu-id="38e71-185">In .NET Core, .NET 5, and ASP.NET Core, this setting is controlled by _runtimeconfig.json_, as shown in the following JSON:</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

<span data-ttu-id="38e71-186">Další informace naleznete v tématu ["nastavení konfigurace runtime .NET Core"](/dotnet/core/run-time-config/).</span><span class="sxs-lookup"><span data-stu-id="38e71-186">For more information, see [".NET Core run-time configuration settings"](/dotnet/core/run-time-config/).</span></span>

<span data-ttu-id="38e71-187">`AllowArbitraryDataSetTypeInstantiation` lze také nastavit programově prostřednictvím [AppContext. SetSwitch](/dotnet/api/system.appcontext.setswitch) namísto použití konfiguračního souboru, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="38e71-187">`AllowArbitraryDataSetTypeInstantiation` can also be set programmatically via [AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) instead of using a configuration file, as shown in the following code:</span></span>

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 <span data-ttu-id="38e71-188">Pokud zvolíte předchozí programový přístup, volání, které `AppContext.SetSwitch` by mělo probíhat na začátku ve spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="38e71-188">If you choose the preceding programmatic approach, the call to `AppContext.SetSwitch` should occur early in the apps startup.</span></span>

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a><span data-ttu-id="38e71-189">V registru v rámci počítače (.NET Framework 2,0-4,8)</span><span class="sxs-lookup"><span data-stu-id="38e71-189">Through the machine-wide registry (.NET Framework 2.0 - 4.8)</span></span>

<span data-ttu-id="38e71-190">Pokud `AppContext` není k dispozici, můžete zakázat kontrolu typu v registru systému Windows:</span><span class="sxs-lookup"><span data-stu-id="38e71-190">If `AppContext` is not available, type limiting checks can be disabled with the Windows registry:</span></span>

* <span data-ttu-id="38e71-191">Správce musí nakonfigurovat registr.</span><span class="sxs-lookup"><span data-stu-id="38e71-191">An administrator must configure the registry.</span></span>
* <span data-ttu-id="38e71-192">Použití registru je změnou celého počítače a bude mít vliv na _všechny_ aplikace běžící v počítači.</span><span class="sxs-lookup"><span data-stu-id="38e71-192">Using the registry is a machine-wide change and will affect _all_ apps running on the machine.</span></span>

| <span data-ttu-id="38e71-193">Typ</span><span class="sxs-lookup"><span data-stu-id="38e71-193">Type</span></span>  |  <span data-ttu-id="38e71-194">Hodnota</span><span class="sxs-lookup"><span data-stu-id="38e71-194">Value</span></span> |
|---|---|
| <span data-ttu-id="38e71-195">**Klíč registru**</span><span class="sxs-lookup"><span data-stu-id="38e71-195">**Registry key**</span></span> | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| <span data-ttu-id="38e71-196">**Název hodnoty**</span><span class="sxs-lookup"><span data-stu-id="38e71-196">**Value name**</span></span> | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| <span data-ttu-id="38e71-197">**Typ hodnoty**</span><span class="sxs-lookup"><span data-stu-id="38e71-197">**Value type**</span></span> | `REG_SZ` |
| <span data-ttu-id="38e71-198">**Údaj hodnoty**</span><span class="sxs-lookup"><span data-stu-id="38e71-198">**Value data**</span></span> | `true` |

<span data-ttu-id="38e71-199">V 64 operačním systému musí být tato hodnota přičtena pro 64 klíč (zobrazený výše) a 32-bitový klíč.</span><span class="sxs-lookup"><span data-stu-id="38e71-199">On a 64-bit operating system, this value my need to be added for both the 64-bit key (shown above) and the 32-bit key.</span></span> <span data-ttu-id="38e71-200">32 bitový klíč se nachází na adrese `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` .</span><span class="sxs-lookup"><span data-stu-id="38e71-200">The 32-bit key is located at `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext`.</span></span>

<span data-ttu-id="38e71-201">Další informace o tom, jak nakonfigurovat registr ke konfiguraci `AppContext` , najdete v tématu ["AppContext pro příjemce knihovny"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span><span class="sxs-lookup"><span data-stu-id="38e71-201">For more information on using the registry to configure `AppContext`, see ["AppContext for library consumers"](/dotnet/api/system.appcontext#appcontext-for-library-consumers).</span></span>

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a><span data-ttu-id="38e71-202">Bezpečnost s ohledem na nedůvěryhodný vstup</span><span class="sxs-lookup"><span data-stu-id="38e71-202">Safety with regard to untrusted input</span></span>

<span data-ttu-id="38e71-203">Nicméně `DataSet` a `DataTable` ukládají výchozí omezení pro typy, které mohou být přítomny při deserializaci datových částí XML __ `DataSet` a `DataTable` obecně nejsou bezpečné, pokud jsou naplněny nedůvěryhodnými vstupy.__</span><span class="sxs-lookup"><span data-stu-id="38e71-203">While `DataSet` and `DataTable` do impose default limitations on the types that are allowed to be present while deserializing XML payloads, __`DataSet` and `DataTable` are in general not safe when populated with untrusted input.__</span></span> <span data-ttu-id="38e71-204">Následující seznam nevyčerpávajících způsobů, jak `DataSet` `DataTable` může instance nebo číst nedůvěryhodný vstup.</span><span class="sxs-lookup"><span data-stu-id="38e71-204">The following is a non-exhaustive list of ways that a `DataSet` or `DataTable` instance might read untrusted input.</span></span>

* <span data-ttu-id="38e71-205">`DataAdapter`Odkazuje na databázi a `DataAdapter.Fill` metoda se používá k naplnění `DataSet` obsahu databázového dotazu.</span><span class="sxs-lookup"><span data-stu-id="38e71-205">A `DataAdapter` references a database, and the `DataAdapter.Fill` method is used to populate a `DataSet` with the contents of a database query.</span></span>
* <span data-ttu-id="38e71-206">`DataSet.ReadXml`Metoda nebo `DataTable.ReadXml` se používá ke čtení souboru XML obsahujícího informace o sloupci a řádku.</span><span class="sxs-lookup"><span data-stu-id="38e71-206">The `DataSet.ReadXml` or `DataTable.ReadXml` method is used to read an XML file containing column and row information.</span></span>
* <span data-ttu-id="38e71-207">`DataSet`Instance nebo `DataTable` je serializována jako součást webových služeb ASP.NET (SOAP) nebo z koncového bodu WCF.</span><span class="sxs-lookup"><span data-stu-id="38e71-207">A `DataSet` or `DataTable` instance is serialized as part of a ASP.NET (SOAP) web services or WCF endpoint.</span></span>
* <span data-ttu-id="38e71-208">Serializátor, jako je například, `XmlSerializer` slouží k deserializaci `DataSet` `DataTable` instance nebo z datového proudu XML.</span><span class="sxs-lookup"><span data-stu-id="38e71-208">A serializer such as `XmlSerializer` is used to deserialize a `DataSet` or `DataTable` instance from an XML stream.</span></span>
* <span data-ttu-id="38e71-209">Serializátor, jako je například, `JsonConvert` slouží k deserializaci `DataSet` `DataTable` instance nebo z datového proudu JSON.</span><span class="sxs-lookup"><span data-stu-id="38e71-209">A serializer such as `JsonConvert` is used to deserialize a `DataSet` or `DataTable` instance from a JSON stream.</span></span> <span data-ttu-id="38e71-210">`JsonConvert` je metoda v oblíbenýchNewtonsoft.Jstřetích stran [ v](https://www.newtonsoft.com/json) knihovně.</span><span class="sxs-lookup"><span data-stu-id="38e71-210">`JsonConvert` is a method in the popular third-party [Newtonsoft.Json](https://www.newtonsoft.com/json) library.</span></span>
* <span data-ttu-id="38e71-211">Serializátor, jako je například, `BinaryFormatter` se používá k deserializaci `DataSet` `DataTable` instance nebo z nezpracovaného bajtového datového proudu.</span><span class="sxs-lookup"><span data-stu-id="38e71-211">A serializer such as `BinaryFormatter` is used to deserialize a `DataSet` or `DataTable` instance from a raw byte stream.</span></span>

<span data-ttu-id="38e71-212">Tento dokument popisuje bezpečnostní požadavky pro předchozí scénáře.</span><span class="sxs-lookup"><span data-stu-id="38e71-212">This document discusses safety considerations for the preceding scenarios.</span></span>

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a><span data-ttu-id="38e71-213">Použijte `DataAdapter.Fill` k naplnění `DataSet` z nedůvěryhodného zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="38e71-213">Use `DataAdapter.Fill` to populate a `DataSet` from an untrusted data source</span></span>

<span data-ttu-id="38e71-214">`DataSet`Instanci lze naplnit `DataAdapter` pomocí [ `DataAdapter.Fill` metody](/dotnet/api/system.data.common.dataadapter.fill), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="38e71-214">A `DataSet` instance can be populated from a `DataAdapter` by using [the `DataAdapter.Fill` method](/dotnet/api/system.data.common.dataadapter.fill), as shown in the following example.</span></span>

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

<span data-ttu-id="38e71-215">(Výše uvedená ukázka kódu je součástí většího vzorku, který byl nalezen při [naplnění datové sady z objektu DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span><span class="sxs-lookup"><span data-stu-id="38e71-215">(The code sample above is part of a larger sample found at [Populating a DataSet from a DataAdapter](../populating-a-dataset-from-a-dataadapter.md).)</span></span>

> <span data-ttu-id="38e71-216">Většina aplikací může zjednodušit a předpokládat, že je jejich databázová vrstva důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="38e71-216">Most apps can simplify and assume that their database layer is trusted.</span></span> <span data-ttu-id="38e71-217">Nicméně, pokud jste [ve výrobním prostředí pro vaše](https://www.microsoft.com/securityengineering/sdl/threatmodeling) aplikace, váš model hrozeb může považovat za hranice důvěry mezi aplikací (klientem) a vrstvou databáze (serverem).</span><span class="sxs-lookup"><span data-stu-id="38e71-217">However, if you are in the habit of [threat modeling](https://www.microsoft.com/securityengineering/sdl/threatmodeling) your apps, your threat model may consider there to be a trust boundary between the application (client) and database layer (server).</span></span> <span data-ttu-id="38e71-218">Použití [vzájemného ověřování](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) nebo [ověřování AAD](/azure/azure-sql/database/authentication-aad-overview) mezi klientem a serverem je jedním ze způsobů, jak pomoci vyřešit rizika spojená s tímto.</span><span class="sxs-lookup"><span data-stu-id="38e71-218">Using [mutual authentication](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections) or [AAD authentication](/azure/azure-sql/database/authentication-aad-overview) between client and server is one way to help address the risks associated with this.</span></span> <span data-ttu-id="38e71-219">Zbývající část této části popisuje možný výsledek připojení klienta k nedůvěryhodnému serveru.</span><span class="sxs-lookup"><span data-stu-id="38e71-219">The remainder of this section discusses the possible result of a client connecting to an untrusted server.</span></span>

<span data-ttu-id="38e71-220">Důsledky ukazatele myši `DataAdapter` na nedůvěryhodný zdroj dat závisí na implementaci `DataAdapter` samotného.</span><span class="sxs-lookup"><span data-stu-id="38e71-220">The consequences of pointing a `DataAdapter` at an untrusted data source depend on the implementation of the `DataAdapter` itself.</span></span>

### <a name="sqldataadapter"></a><span data-ttu-id="38e71-221">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="38e71-221">SqlDataAdapter</span></span>

<span data-ttu-id="38e71-222">Pro předdefinovaný typ [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), který odkazuje na nedůvěryhodný zdroj dat, by mohlo dojít k útokům DOS (Denial of Service).</span><span class="sxs-lookup"><span data-stu-id="38e71-222">For the built-in type [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter), referencing an untrusted data source could result in a denial of service (DoS) attack.</span></span> <span data-ttu-id="38e71-223">Útok DoS by mohl způsobit, že aplikace přestane reagovat nebo dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="38e71-223">The DoS attack could result in the app becoming unresponsive or crashing.</span></span> <span data-ttu-id="38e71-224">Pokud může útočník vysázet knihovnu DLL společně s aplikací, mohou být také schopny dosáhnout místního spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-224">If an attacker can plant a DLL alongside the app, they may also be able to achieve local code execution.</span></span>

### <a name="other-dataadapter-types"></a><span data-ttu-id="38e71-225">Jiné typy DataAdapter</span><span class="sxs-lookup"><span data-stu-id="38e71-225">Other DataAdapter types</span></span>

<span data-ttu-id="38e71-226">Implementace třetích stran `DataAdapter` musí učinit vlastní posouzení o tom, jaké záruky zabezpečení poskytují na tvář nedůvěryhodných vstupů.</span><span class="sxs-lookup"><span data-stu-id="38e71-226">Third-party `DataAdapter` implementations must make their own assessments about what security guarantees they provide in the face of untrusted inputs.</span></span> <span data-ttu-id="38e71-227">Rozhraní .NET nemůže žádným bezpečnostním zárukám souvisejícím s těmito implementacemi dělat.</span><span class="sxs-lookup"><span data-stu-id="38e71-227">.NET cannot make any safety guarantees regarding these implementations.</span></span>

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a><span data-ttu-id="38e71-228">DataSet. ReadXml a DataTable. ReadXml</span><span class="sxs-lookup"><span data-stu-id="38e71-228">DataSet.ReadXml and DataTable.ReadXml</span></span>

<span data-ttu-id="38e71-229">`DataSet.ReadXml`Metody a `DataTable.ReadXml` nejsou bezpečné při použití s nedůvěryhodným vstupem.</span><span class="sxs-lookup"><span data-stu-id="38e71-229">The `DataSet.ReadXml` and `DataTable.ReadXml` methods are not safe when used with untrusted input.</span></span> <span data-ttu-id="38e71-230">Důrazně doporučujeme, aby spotřebitelé místo toho měli možnost použít jednu z alternativ uvedených v tomto dokumentu později.</span><span class="sxs-lookup"><span data-stu-id="38e71-230">We strongly recommend that consumers instead consider using one of the alternatives outlined later in this document.</span></span>

<span data-ttu-id="38e71-231">Implementace `DataSet.ReadXml` a `DataTable.ReadXml` byly původně vytvořené před chybami zabezpečení serializace byly dobře srozumitelnější kategorie hrozeb.</span><span class="sxs-lookup"><span data-stu-id="38e71-231">The implementations of `DataSet.ReadXml` and `DataTable.ReadXml` were originally created before serialization vulnerabilities were a well-understood threat category.</span></span> <span data-ttu-id="38e71-232">V důsledku toho kód nedodržuje aktuální osvědčené postupy zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="38e71-232">As a result, the code does not follow current security best practices.</span></span> <span data-ttu-id="38e71-233">Tato rozhraní API je možné použít jako vektory pro útočníky k provádění útoků DoS proti webovým aplikacím.</span><span class="sxs-lookup"><span data-stu-id="38e71-233">These APIs can be used as vectors for attackers to perform DoS attacks against web apps.</span></span> <span data-ttu-id="38e71-234">Tyto útoky mohou vykreslovat webovou službu jako nereagující nebo vést k neočekávanému ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="38e71-234">These attacks might render the web service unresponsive or result in unexpected process termination.</span></span> <span data-ttu-id="38e71-235">Rozhraní neposkytuje omezení pro tyto kategorie útoků a rozhraní .NET toto chování považuje za "podle návrhu".</span><span class="sxs-lookup"><span data-stu-id="38e71-235">The framework does not provide mitigations for these attack categories and .NET considers this behavior "by design".</span></span>

<span data-ttu-id="38e71-236">Rozhraní .NET vydala aktualizace zabezpečení, které umožňují zmírnit některé problémy, například vyzrazení informací nebo vzdálené spuštění kódu v `DataSet.ReadXml` a `DataTable.ReadXml` .</span><span class="sxs-lookup"><span data-stu-id="38e71-236">.NET has released security updates to mitigate some issues such as information disclosure or remote code execution in `DataSet.ReadXml` and `DataTable.ReadXml`.</span></span> <span data-ttu-id="38e71-237">Aktualizace zabezpečení .NET nemusí poskytovat kompletní ochranu proti těmto kategoriím hrozeb.</span><span class="sxs-lookup"><span data-stu-id="38e71-237">The .NET security updates may not provide complete protection against these threat categories.</span></span> <span data-ttu-id="38e71-238">Spotřebitelé by měli vyhodnotit své jednotlivé scénáře a vzít v úvahu potenciální ozáření těchto rizik.</span><span class="sxs-lookup"><span data-stu-id="38e71-238">Consumers should assess their individual scenarios and consider their potential exposure to these risks.</span></span>

<span data-ttu-id="38e71-239">Spotřebitelé by měli vědět, že aktualizace zabezpečení těchto rozhraní API můžou v některých situacích ovlivnit kompatibilitu aplikací.</span><span class="sxs-lookup"><span data-stu-id="38e71-239">Consumers should be aware that security updates to these APIs may impact application compatibility in some situations.</span></span> <span data-ttu-id="38e71-240">Kromě toho existuje možnost, že se zjistí nová chyba zabezpečení v těchto rozhraních API, pro kterou .NET nedokáže prakticky publikovat aktualizaci zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="38e71-240">Furthermore, the possibility exists that a novel vulnerability in these APIs will be discovered for which .NET can't practically publish a security update.</span></span>

<span data-ttu-id="38e71-241">Zákazníkům těchto rozhraní API doporučujeme:</span><span class="sxs-lookup"><span data-stu-id="38e71-241">We recommend that consumers of these APIs either:</span></span>

* <span data-ttu-id="38e71-242">Zvažte použití jedné z alternativ uvedených níže v tomto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="38e71-242">Consider using one of the alternatives outlined later in this document.</span></span>
* <span data-ttu-id="38e71-243">Provádějte individuální posouzení rizik na svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="38e71-243">Perform individual risk assessments on their apps.</span></span>

<span data-ttu-id="38e71-244">K určení, jestli se mají používat tato rozhraní API, se jedná výhradně o zodpovědnost spotřebitele.</span><span class="sxs-lookup"><span data-stu-id="38e71-244">It is the consumer's sole responsibility to determine whether to utilize these APIs.</span></span> <span data-ttu-id="38e71-245">Spotřebitelé by měli vyhodnotit jakákoli bezpečnostní, technická a zákonná rizika, včetně regulativních požadavků, které mohou doprovázet pomocí těchto rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="38e71-245">Consumers should assess any security, technical, and legal risks, including regulatory requirements, that may accompany using these APIs.</span></span>

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a><span data-ttu-id="38e71-246">Datová sada a DataTable prostřednictvím webových služeb ASP.NET nebo WCF</span><span class="sxs-lookup"><span data-stu-id="38e71-246">DataSet and DataTable via ASP.NET web services or WCF</span></span>

<span data-ttu-id="38e71-247">Je možné přijmout `DataSet` `DataTable` instanci nebo instance v rámci webové služby ASP.NET (SOAP), jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="38e71-247">It is possible to accept a `DataSet` or a `DataTable` instance in an ASP.NET (SOAP) web service, as demonstrated in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

<span data-ttu-id="38e71-248">Variace v této podobě není akceptovat `DataSet` ani `DataTable` přímo jako parametr, ale místo toho ji přijmout jako součást celkového grafu serializovaného objektu SOAP, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="38e71-248">A variation on this is not to accept `DataSet` or `DataTable` directly as a parameter, but instead to accept it as part of the overall SOAP serialized object graph, as shown in the following code:</span></span>

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="38e71-249">Nebo pomocí služby WCF namísto webových služeb ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="38e71-249">Or, using WCF instead of ASP.NET web services:</span></span>

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="38e71-250">Ve všech těchto případech jsou modely hrozeb a záruky zabezpečení stejné jako v [části DataSet. ReadXml a DataTable. ReadXml](#dsrdtr).</span><span class="sxs-lookup"><span data-stu-id="38e71-250">In all of these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr).</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a><span data-ttu-id="38e71-251">Deserializace datové sady nebo objektu DataTable přes XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="38e71-251">Deserialize a DataSet or DataTable via XmlSerializer</span></span>

<span data-ttu-id="38e71-252">Vývojáři mohou použít `XmlSerializer` k deserializaci `DataSet` a `DataTable` instancí, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="38e71-252">Developers can use `XmlSerializer` to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="38e71-253">V těchto případech jsou modely hrozeb a záruky zabezpečení stejné jako v [části DataSet. ReadXml a DataTable. ReadXml.](#dsrdtr)</span><span class="sxs-lookup"><span data-stu-id="38e71-253">In these cases, the threat model and security guarantees are the same as the [DataSet.ReadXml and DataTable.ReadXml section](#dsrdtr)</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a><span data-ttu-id="38e71-254">Deserializace datové sady nebo objektu DataTable prostřednictvím JsonConvert</span><span class="sxs-lookup"><span data-stu-id="38e71-254">Deserialize a DataSet or DataTable via JsonConvert</span></span>

<span data-ttu-id="38e71-255">Oblíbená [Knihovna Newtonsoft](https://www.newtonsoft.com/json) třetí strany se dá použít k deserializaci `DataSet` a `DataTable` instancím, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="38e71-255">The popular third-party Newtonsoft library [JSON.NET](https://www.newtonsoft.com/json) can be used to deserialize `DataSet` and `DataTable` instances, as shown in the following code:</span></span>

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

<span data-ttu-id="38e71-256">Deserializace `DataSet` nebo `DataTable` tímto způsobem z nedůvěryhodného objektu BLOB JSON není bezpečná.</span><span class="sxs-lookup"><span data-stu-id="38e71-256">Deserializing a `DataSet` or `DataTable` in this manner from an untrusted JSON blob is not safe.</span></span> <span data-ttu-id="38e71-257">Tento model je zranitelný vůči útokům DOS (Denial of Service).</span><span class="sxs-lookup"><span data-stu-id="38e71-257">This pattern is vulnerable to a denial of service attack.</span></span> <span data-ttu-id="38e71-258">Takový útok může způsobit chybu aplikace nebo vykreslování, která neodpovídá.</span><span class="sxs-lookup"><span data-stu-id="38e71-258">Such an attack could crash the app or render it unresponsive.</span></span>

> [!NOTE]
> <span data-ttu-id="38e71-259">Společnost Microsoft nezaručuje ani nepodporuje implementaci knihoven třetích stran, jako je _Newtonsoft.Js_.</span><span class="sxs-lookup"><span data-stu-id="38e71-259">Microsoft does not warrant or support the implementation of third-party libraries like _Newtonsoft.Json_.</span></span> <span data-ttu-id="38e71-260">Tyto informace jsou k dispozici pro úplnost a jsou přesné v době psaní tohoto zápisu.</span><span class="sxs-lookup"><span data-stu-id="38e71-260">This information is provided for completeness and is accurate as of the time of this writing.</span></span>

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a><span data-ttu-id="38e71-261">Deserializace datové sady nebo objektu DataTable prostřednictvím BinaryFormatter</span><span class="sxs-lookup"><span data-stu-id="38e71-261">Deserialize a DataSet or DataTable via BinaryFormatter</span></span>

<span data-ttu-id="38e71-262">`BinaryFormatter` `NetDataContractSerializer` `SoapFormatter` Pro ***unsafe*** deserializaci `DataSet` `DataTable` instance nebo z nedůvěryhodné datové části nesmějí vývojáři nikdy používat,, ani související nezabezpečené formátovací moduly:</span><span class="sxs-lookup"><span data-stu-id="38e71-262">Developers must never use `BinaryFormatter`, `NetDataContractSerializer`, `SoapFormatter`, or related ***unsafe*** formatters to deserialize a `DataSet` or `DataTable` instance from an untrusted payload:</span></span>

* <span data-ttu-id="38e71-263">To je náchylné k úplnému útoku vzdáleného spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-263">This is susceptible to a full remote code execution attack.</span></span>
* <span data-ttu-id="38e71-264">Použití vlastní není `SerializationBinder` dostačující k tomu, aby se zabránilo takovým útokům.</span><span class="sxs-lookup"><span data-stu-id="38e71-264">Using a custom `SerializationBinder` is not sufficient to prevent such an attack.</span></span>

## <a name="safe-replacements"></a><span data-ttu-id="38e71-265">Bezpečné náhrady</span><span class="sxs-lookup"><span data-stu-id="38e71-265">Safe replacements</span></span>

<span data-ttu-id="38e71-266">Pro aplikace, které:</span><span class="sxs-lookup"><span data-stu-id="38e71-266">For apps that either:</span></span>

* <span data-ttu-id="38e71-267">Přijměte `DataSet` nebo prostřednictvím koncového `DataTable` bodu protokolu SOAP. asmx nebo koncového bodu WCF.</span><span class="sxs-lookup"><span data-stu-id="38e71-267">Accept `DataSet` or `DataTable` through an .asmx SOAP endpoint or a WCF endpoint.</span></span>
* <span data-ttu-id="38e71-268">Deserializace nedůvěryhodných dat do instance `DataSet` nebo `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="38e71-268">Deserialize untrusted data into an instance of `DataSet` or `DataTable`.</span></span>

<span data-ttu-id="38e71-269">Zvažte nahrazení objektového modelu, který chcete použít [Entity Framework](/ef).</span><span class="sxs-lookup"><span data-stu-id="38e71-269">Consider replacing the object model to use [Entity Framework](/ef).</span></span> <span data-ttu-id="38e71-270">Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="38e71-270">Entity Framework:</span></span>

* <span data-ttu-id="38e71-271">Je bohatě moderní rozhraní orientované na objekty, které může představovat relační data.</span><span class="sxs-lookup"><span data-stu-id="38e71-271">Is a rich, modern, object-oriented framework that can represent relational data.</span></span>
* <span data-ttu-id="38e71-272">Přináší [různorodý ekosystém](/ef/core/providers/) zprostředkovatelů databází, aby bylo možné snadno projektovat databázové dotazy pomocí vašich entity Frameworkch objektových modelů.</span><span class="sxs-lookup"><span data-stu-id="38e71-272">Brings [a diverse ecosystem](/ef/core/providers/) of database providers to make it easy to project database queries via your Entity Framework object models.</span></span>
* <span data-ttu-id="38e71-273">Nabízí integrované ochrany při deserializaci dat z nedůvěryhodných zdrojů.</span><span class="sxs-lookup"><span data-stu-id="38e71-273">Offers built-in protections when deserializing data from untrusted sources.</span></span>

<span data-ttu-id="38e71-274">Pro aplikace, které používají `.aspx` koncové body SOAP, zvažte změnu těchto koncových bodů tak, aby používaly [WCF](/dotnet/framework/wcf/).</span><span class="sxs-lookup"><span data-stu-id="38e71-274">For apps that use `.aspx` SOAP endpoints, consider changing those endpoints to use [WCF](/dotnet/framework/wcf/).</span></span> <span data-ttu-id="38e71-275">Služba WCF je plně vybavená náhrada za `.asmx` webové služby.</span><span class="sxs-lookup"><span data-stu-id="38e71-275">WCF is a more fully featured replacement for `.asmx` web services.</span></span> <span data-ttu-id="38e71-276">Koncové body WCF [je možné zveřejnit prostřednictvím protokolu SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) kvůli kompatibilitě se stávajícími volajícími.</span><span class="sxs-lookup"><span data-stu-id="38e71-276">WCF endpoints [can be exposed via SOAP](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md) for compatibility with existing callers.</span></span>

## <a name="code-analyzers"></a><span data-ttu-id="38e71-277">Analyzátory kódu</span><span class="sxs-lookup"><span data-stu-id="38e71-277">Code analyzers</span></span>

<span data-ttu-id="38e71-278">Pravidla zabezpečení analyzátoru kódu, která se spouštějí při kompilaci zdrojového kódu, mohou pomáhat najít ohrožení zabezpečení související s tímto problémem zabezpečení v jazyce C# a Visual Basic kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-278">Code analyzer security rules, which run when your source code is compiled, can help to find vulnerabilities related to this security issue in C# and Visual Basic code.</span></span> <span data-ttu-id="38e71-279">Microsoft. CodeAnalysis. FxCopAnalyzers je balíček NuGet analyzátorů kódu, který je distribuován v [NuGet.org](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="38e71-279">Microsoft.CodeAnalysis.FxCopAnalyzers is a NuGet package of code analyzers that's distributed on [nuget.org](https://www.nuget.org/).</span></span>

<span data-ttu-id="38e71-280">Přehled analyzátorů kódu najdete v tématu [Přehled analyzátorů zdrojového kódu](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span><span class="sxs-lookup"><span data-stu-id="38e71-280">For an overview of code analyzers, see [Overview of source code analyzers](https://docs.microsoft.com/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

<span data-ttu-id="38e71-281">Povolte následující pravidla Microsoft. CodeAnalysis. FxCopAnalyzers:</span><span class="sxs-lookup"><span data-stu-id="38e71-281">Enable the following Microsoft.CodeAnalysis.FxCopAnalyzers rules:</span></span>

- <span data-ttu-id="38e71-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): Nepoužívejte DataTable. ReadXml () s nedůvěryhodnými daty</span><span class="sxs-lookup"><span data-stu-id="38e71-282">[CA2350](https://docs.microsoft.com/visualstudio/code-quality/ca2350): Do not use DataTable.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="38e71-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): Nepoužívejte DataSet. ReadXml () s nedůvěryhodnými daty</span><span class="sxs-lookup"><span data-stu-id="38e71-283">[CA2351](https://docs.microsoft.com/visualstudio/code-quality/ca2351): Do not use DataSet.ReadXml() with untrusted data</span></span>
- <span data-ttu-id="38e71-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): nebezpečná datová sada nebo DataTable v serializovatelným typu může být zranitelná vůči útokům na vzdálené spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-284">[CA2352](https://docs.microsoft.com/visualstudio/code-quality/ca2352): Unsafe DataSet or DataTable in serializable type can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="38e71-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): nebezpečná datová sada nebo DataTable v serializovatelným typu</span><span class="sxs-lookup"><span data-stu-id="38e71-285">[CA2353](https://docs.microsoft.com/visualstudio/code-quality/ca2353): Unsafe DataSet or DataTable in serializable type</span></span>
- <span data-ttu-id="38e71-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): nebezpečná datová sada nebo DataTable v deserializovaném objektovém grafu může být zranitelná vůči útokům na vzdálené spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-286">[CA2354](https://docs.microsoft.com/visualstudio/code-quality/ca2354): Unsafe DataSet or DataTable in deserialized object graph can be vulnerable to remote code execution attacks</span></span>
- <span data-ttu-id="38e71-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): v grafu deserializovatelných objektů se našel nezabezpečená datová sada nebo typ DataTable.</span><span class="sxs-lookup"><span data-stu-id="38e71-287">[CA2355](https://docs.microsoft.com/visualstudio/code-quality/ca2355): Unsafe DataSet or DataTable type found in deserializable object graph</span></span>
- <span data-ttu-id="38e71-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): nebezpečná datová sada nebo typ DataTable ve webovém deserializaci objektu grafu</span><span class="sxs-lookup"><span data-stu-id="38e71-288">[CA2356](https://docs.microsoft.com/visualstudio/code-quality/ca2356): Unsafe DataSet or DataTable type in web deserializable object graph</span></span>
- <span data-ttu-id="38e71-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Ujistěte se, že automaticky vygenerovaná třída obsahující DataSet. ReadXml () se nepoužívá s nedůvěryhodnými daty.</span><span class="sxs-lookup"><span data-stu-id="38e71-289">[CA2361](https://docs.microsoft.com/visualstudio/code-quality/ca2361): Ensure autogenerated class containing DataSet.ReadXml() is not used with untrusted data</span></span>
- <span data-ttu-id="38e71-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): nebezpečná datová sada nebo DataTable v automaticky generovaném serializovatelným typu může být zranitelná proti útokům na vzdálené spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="38e71-290">[CA2362](https://docs.microsoft.com/visualstudio/code-quality/ca2362): Unsafe DataSet or DataTable in autogenerated serializable type can be vulnerable to remote code execution attacks</span></span>

<span data-ttu-id="38e71-291">Další informace o konfiguraci pravidel najdete v tématu [použití analyzátorů kódu](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span><span class="sxs-lookup"><span data-stu-id="38e71-291">For more information about configuring rules, see [Use code analyzers](https://docs.microsoft.com/visualstudio/code-quality/use-roslyn-analyzers).</span></span>

<span data-ttu-id="38e71-292">Nová pravidla zabezpečení jsou k dispozici v následujících balíčcích NuGet:</span><span class="sxs-lookup"><span data-stu-id="38e71-292">The new security rules are available in the following NuGet packages:</span></span>

- <span data-ttu-id="38e71-293">Microsoft. CodeAnalysis. FxCopAnalyzers 3.3.0: pro Visual Studio 2019 verze 16,3 nebo novější</span><span class="sxs-lookup"><span data-stu-id="38e71-293">Microsoft.CodeAnalysis.FxCopAnalyzers 3.3.0: for Visual Studio 2019 version 16.3 or later</span></span>
- <span data-ttu-id="38e71-294">Microsoft. CodeAnalysis. FxCopAnalyzers 2.9.11: pro Visual Studio 2017 verze 15,9 nebo novější</span><span class="sxs-lookup"><span data-stu-id="38e71-294">Microsoft.CodeAnalysis.FxCopAnalyzers 2.9.11: for Visual Studio 2017 version 15.9 or later</span></span>
