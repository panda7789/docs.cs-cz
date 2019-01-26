---
title: Schéma nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: a74716bcdf3c85c08d0ff3bf66407dce30ee91cc
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083467"
---
# <a name="application-settings-schema"></a><span data-ttu-id="d90c7-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="d90c7-102">Application Settings schema</span></span>

<span data-ttu-id="d90c7-103">Nastavení aplikace umožňují aplikace Windows Forms nebo technologii ASP.NET ukládat a načítat nastavení s rozsahem aplikace a nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="d90c7-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="d90c7-104">V tomto kontextu *nastavení* libovolné informace, které může být specifické pro aplikaci nebo specifické pro aktuálního uživatele je – vše od připojovací řetězec databáze pro uživatele upřednostňovaného výchozí velikost okna.</span><span class="sxs-lookup"><span data-stu-id="d90c7-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="d90c7-105">Ve výchozím nastavení aplikace v aplikaci Windows Forms používá <xref:System.Configuration.LocalFileSettingsProvider> třídu, která využívá konfigurační systém .NET k ukládání nastavení do konfiguračního souboru XML.</span><span class="sxs-lookup"><span data-stu-id="d90c7-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="d90c7-106">Další informace o souborech, které používají nastavení aplikace najdete v tématu [architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="d90c7-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="d90c7-107">Nastavení aplikace definuje následující prvky jako součást konfigurační soubory, které používá.</span><span class="sxs-lookup"><span data-stu-id="d90c7-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="d90c7-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="d90c7-108">Element</span></span>                    | <span data-ttu-id="d90c7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d90c7-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="d90c7-110">**\<applicationSettings>**</span><span class="sxs-lookup"><span data-stu-id="d90c7-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="d90c7-111">Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d90c7-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="d90c7-112">**\<userSettings>**</span><span class="sxs-lookup"><span data-stu-id="d90c7-112">**\<userSettings>**</span></span>        | <span data-ttu-id="d90c7-113">Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="d90c7-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="d90c7-114">**\<setting>**</span><span class="sxs-lookup"><span data-stu-id="d90c7-114">**\<setting>**</span></span>             | <span data-ttu-id="d90c7-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="d90c7-115">Defines a setting.</span></span> <span data-ttu-id="d90c7-116">Podřízené buď  **\<applicationSettings >** nebo  **\<userSettings >**.</span><span class="sxs-lookup"><span data-stu-id="d90c7-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="d90c7-117">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="d90c7-117">**\<value>**</span></span>               | <span data-ttu-id="d90c7-118">Definuje hodnoty nastavení.</span><span class="sxs-lookup"><span data-stu-id="d90c7-118">Defines a setting's value.</span></span> <span data-ttu-id="d90c7-119">Podřízený  **\<Nastavení >**.</span><span class="sxs-lookup"><span data-stu-id="d90c7-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="d90c7-120">\<applicationSettings > – element</span><span class="sxs-lookup"><span data-stu-id="d90c7-120">\<applicationSettings> element</span></span>

<span data-ttu-id="d90c7-121">Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro instanci aplikace na klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="d90c7-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="d90c7-122">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="d90c7-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="d90c7-123">\<userSettings > – element</span><span class="sxs-lookup"><span data-stu-id="d90c7-123">\<userSettings> element</span></span>

<span data-ttu-id="d90c7-124">Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro uživatele, který právě používá aplikace.</span><span class="sxs-lookup"><span data-stu-id="d90c7-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="d90c7-125">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="d90c7-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="d90c7-126">\<Nastavení > – element</span><span class="sxs-lookup"><span data-stu-id="d90c7-126">\<setting> element</span></span>

<span data-ttu-id="d90c7-127">Tento prvek definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="d90c7-127">This element defines a setting.</span></span> <span data-ttu-id="d90c7-128">Má následující atributy.</span><span class="sxs-lookup"><span data-stu-id="d90c7-128">It has the following attributes.</span></span>

| <span data-ttu-id="d90c7-129">Atribut</span><span class="sxs-lookup"><span data-stu-id="d90c7-129">Attribute</span></span>        | <span data-ttu-id="d90c7-130">Popis</span><span class="sxs-lookup"><span data-stu-id="d90c7-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="d90c7-131">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="d90c7-131">**name**</span></span>         | <span data-ttu-id="d90c7-132">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d90c7-132">Required.</span></span> <span data-ttu-id="d90c7-133">Jedinečné ID nastavení.</span><span class="sxs-lookup"><span data-stu-id="d90c7-133">The unique ID of the setting.</span></span> <span data-ttu-id="d90c7-134">Nastavení vytvořená pomocí sady Visual Studio se uloží s názvem `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="d90c7-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="d90c7-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="d90c7-135">**serializedAs**</span></span> | <span data-ttu-id="d90c7-136">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d90c7-136">Required.</span></span> <span data-ttu-id="d90c7-137">Formát, který se má použít pro serializaci hodnotu na text.</span><span class="sxs-lookup"><span data-stu-id="d90c7-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="d90c7-138">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="d90c7-138">Valid values are:</span></span><br><br><span data-ttu-id="d90c7-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="d90c7-139">- `string`.</span></span> <span data-ttu-id="d90c7-140">Hodnota je serializován jako řetězec pomocí <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="d90c7-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="d90c7-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="d90c7-141">- `xml`.</span></span> <span data-ttu-id="d90c7-142">Hodnota je serializována použití serializace XML.</span><span class="sxs-lookup"><span data-stu-id="d90c7-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="d90c7-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="d90c7-143">- `binary`.</span></span> <span data-ttu-id="d90c7-144">Hodnota je serializována jako binární kódování textu pomocí binární serializace.</span><span class="sxs-lookup"><span data-stu-id="d90c7-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="d90c7-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="d90c7-145">- `custom`.</span></span> <span data-ttu-id="d90c7-146">Poskytovatel nastavení má vlastní znalostní báze tohoto nastavení a serializuje a deserializuje.</span><span class="sxs-lookup"><span data-stu-id="d90c7-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="d90c7-147">\<Hodnota > – element</span><span class="sxs-lookup"><span data-stu-id="d90c7-147">\<value> element</span></span>

<span data-ttu-id="d90c7-148">Tento prvek obsahuje hodnoty nastavení.</span><span class="sxs-lookup"><span data-stu-id="d90c7-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="d90c7-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="d90c7-149">Example</span></span>

<span data-ttu-id="d90c7-150">Následující příklad ukazuje soubor nastavení aplikace, která definuje dvě nastavení s rozsahem aplikace a dvě nastavení rozsahu uživatele:</span><span class="sxs-lookup"><span data-stu-id="d90c7-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d90c7-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d90c7-151">See also</span></span>

- [<span data-ttu-id="d90c7-152">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="d90c7-152">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="d90c7-153">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="d90c7-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
