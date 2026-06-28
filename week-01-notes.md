# Tydzień 1 — Lab 1: Linux VM + nginx

## Co zrobiłem
- Postawiłem VM (Ubuntu) na Azure przez CLI
- Zainstalowałem nginx, otworzyłem port 80
- Serwowałem własną stronę z chmury
- Posprzątałem zasoby (az group delete)

## Najważniejsza lekcja
Konto free trial blokuje stare maszyny B-series → błąd `NotAvailableForSubscription`.
Rozwiązanie: użyć nowszej serii (Standard_B2s_v2) albo sprawdzić dostępność:
`az vm list-skus --location <region> --size Standard_B --all -o table`
i wybrać rozmiar z kolumną Restrictions = None.

## Komendy które zadziałały
az group create --name lab1-vm --location swedencentral
az vm create --resource-group lab1-vm --name myvm --image Ubuntu2204 --size Standard_B2s_v2 --location swedencentral --admin-username azureuser --generate-ssh-keys --public-ip-sku Standard
az vm open-port --resource-group lab1-vm --name myvm --port 80