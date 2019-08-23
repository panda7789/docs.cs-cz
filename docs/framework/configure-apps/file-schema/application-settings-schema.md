---
title: Schéma nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927753"
---
# <a name="application-settings-schema"></a><span data-ttu-id="5d18d-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5d18d-102">Application Settings schema</span></span>

<span data-ttu-id="5d18d-103">Nastavení aplikace umožňuje aplikaci model Windows Forms nebo ASP.NET ukládat a načítat nastavení s rozsahem aplikace a uživatelem.</span><span class="sxs-lookup"><span data-stu-id="5d18d-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="5d18d-104">V tomto kontextu je *nastavením* jakékoli informace, které mohou být specifické pro aplikaci nebo specifické pro aktuálního uživatele – cokoli z databázového připojovacího řetězce až po upřednostňovanou výchozí velikost okna uživatele.</span><span class="sxs-lookup"><span data-stu-id="5d18d-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="5d18d-105">Ve výchozím nastavení používá <xref:System.Configuration.LocalFileSettingsProvider> nastavení aplikace v model Windows Forms aplikace třídu, která používá konfigurační systém .NET k ukládání nastavení v konfiguračním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5d18d-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="5d18d-106">Další informace o souborech používaných nastavením aplikace najdete v tématu [Architektura nastavení aplikace](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="5d18d-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="5d18d-107">Nastavení aplikace definuje následující prvky jako součást konfiguračních souborů, které používá.</span><span class="sxs-lookup"><span data-stu-id="5d18d-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="5d18d-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="5d18d-108">Element</span></span>                    | <span data-ttu-id="5d18d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="5d18d-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="5d18d-110">**\<applicationSettings>**</span><span class="sxs-lookup"><span data-stu-id="5d18d-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="5d18d-111">Obsahuje všechna  **\<nastavení >** značek specifických pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5d18d-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="5d18d-112">**\<userSettings>**</span><span class="sxs-lookup"><span data-stu-id="5d18d-112">**\<userSettings>**</span></span>        | <span data-ttu-id="5d18d-113">Obsahuje všechna  **\<nastavení >** značek specifických pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="5d18d-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="5d18d-114">**\<Nastavení >**</span><span class="sxs-lookup"><span data-stu-id="5d18d-114">**\<setting>**</span></span>             | <span data-ttu-id="5d18d-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="5d18d-115">Defines a setting.</span></span> <span data-ttu-id="5d18d-116">Podřízená položka buď  **\<ApplicationSettings >** nebo  **\<UserSettings >** .</span><span class="sxs-lookup"><span data-stu-id="5d18d-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="5d18d-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="5d18d-117">**\<value>**</span></span>               | <span data-ttu-id="5d18d-118">Definuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="5d18d-118">Defines a setting's value.</span></span> <span data-ttu-id="5d18d-119">Podřízená položka  **Nastavení>.\<**</span><span class="sxs-lookup"><span data-stu-id="5d18d-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="5d18d-120">\<applicationSettings – element ></span><span class="sxs-lookup"><span data-stu-id="5d18d-120">\<applicationSettings> element</span></span>

<span data-ttu-id="5d18d-121">Tento prvek obsahuje všechna  **\<nastavení >** značek, které jsou specifické pro instanci aplikace v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="5d18d-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="5d18d-122">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="5d18d-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="5d18d-123">\<userSettings – element ></span><span class="sxs-lookup"><span data-stu-id="5d18d-123">\<userSettings> element</span></span>

<span data-ttu-id="5d18d-124">Tento prvek obsahuje všechna  **\<nastavení >** značek, které jsou specifické pro uživatele, který aktuálně používá aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5d18d-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="5d18d-125">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="5d18d-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="5d18d-126">\<nastavení elementu ></span><span class="sxs-lookup"><span data-stu-id="5d18d-126">\<setting> element</span></span>

<span data-ttu-id="5d18d-127">Tento prvek definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="5d18d-127">This element defines a setting.</span></span> <span data-ttu-id="5d18d-128">Má následující atributy.</span><span class="sxs-lookup"><span data-stu-id="5d18d-128">It has the following attributes.</span></span>

| <span data-ttu-id="5d18d-129">Atribut</span><span class="sxs-lookup"><span data-stu-id="5d18d-129">Attribute</span></span>        | <span data-ttu-id="5d18d-130">Popis</span><span class="sxs-lookup"><span data-stu-id="5d18d-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="5d18d-131">**name**</span><span class="sxs-lookup"><span data-stu-id="5d18d-131">**name**</span></span>         | <span data-ttu-id="5d18d-132">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5d18d-132">Required.</span></span> <span data-ttu-id="5d18d-133">Jedinečné ID nastavení</span><span class="sxs-lookup"><span data-stu-id="5d18d-133">The unique ID of the setting.</span></span> <span data-ttu-id="5d18d-134">Nastavení vytvořená pomocí sady Visual Studio se ukládají s `ProjectName.Properties.Settings`názvem.</span><span class="sxs-lookup"><span data-stu-id="5d18d-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="5d18d-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="5d18d-135">**serializedAs**</span></span> | <span data-ttu-id="5d18d-136">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="5d18d-136">Required.</span></span> <span data-ttu-id="5d18d-137">Formát, který má být použit pro serializaci hodnoty na text.</span><span class="sxs-lookup"><span data-stu-id="5d18d-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="5d18d-138">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5d18d-138">Valid values are:</span></span><br><br><span data-ttu-id="5d18d-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="5d18d-139">- `string`.</span></span> <span data-ttu-id="5d18d-140">Hodnota je serializována jako řetězec pomocí <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="5d18d-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="5d18d-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="5d18d-141">- `xml`.</span></span> <span data-ttu-id="5d18d-142">Hodnota je serializovaná pomocí serializace XML.</span><span class="sxs-lookup"><span data-stu-id="5d18d-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="5d18d-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="5d18d-143">- `binary`.</span></span> <span data-ttu-id="5d18d-144">Hodnota je serializována jako textový soubor s kódováním pomocí binární serializace.</span><span class="sxs-lookup"><span data-stu-id="5d18d-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="5d18d-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="5d18d-145">- `custom`.</span></span> <span data-ttu-id="5d18d-146">Poskytovatel nastavení má znalosti tohoto nastavení a serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="5d18d-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="5d18d-147">\<Value – element ></span><span class="sxs-lookup"><span data-stu-id="5d18d-147">\<value> element</span></span>

<span data-ttu-id="5d18d-148">Tento prvek obsahuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="5d18d-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="5d18d-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d18d-149">Example</span></span>

<span data-ttu-id="5d18d-150">Následující příklad ukazuje soubor nastavení aplikace, který definuje dvě nastavení rozsahu aplikace a dvě nastavení v uživatelském rozsahu:</span><span class="sxs-lookup"><span data-stu-id="5d18d-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5d18d-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d18d-151">See also</span></span>

- [<span data-ttu-id="5d18d-152">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5d18d-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="5d18d-153">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5d18d-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
